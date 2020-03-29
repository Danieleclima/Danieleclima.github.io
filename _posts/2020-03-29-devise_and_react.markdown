---
layout: post
title:      "Devise and React"
date:       2020-03-29 16:59:27 +0000
permalink:  devise_and_react
---


I made it! I'm now a graduated Flatiron student searching for a new adventure in the software development industry. The course I started roughtly a year ago may be over but my career as a software engineer has only started and I'm glad it is that way since I love a challengue and it seems like my path is going to be full of roadblocks and problems which require an elegant coding solution.

I'm still working on polishing some of my final projects and filling some knowledge gaps, partly because I needed to remind myself about Ruby and SQL syntaxt since those where the first two languages I studied. Hence it had been a while since the last time I used them.

For my final project I built a React progressive web applicattion that was using Ruby on Rails as an API, In the begining I created my own authentication system that was based on just a User and an Sessions controller (I've pasted the code below) however I later realized that I need a more robust and battle-tested authentication system which is why I decided to use Devise:

```
class SessionsController < ApplicationController
  include CurrentUserConcern

    def create
      binding.pry
      user = User.find_by(:email => params[:user][:email])
      session[:user_id] = user.id
      if user.authenticate
        render json: user
      end
    end

    def logged_in
      if @current_user
        render json: {
          logged_in: true,
          user: @current_user
        }
      else
        render json: {
          logged_in: false
        }
      end
    end
end
```

Devise is a flexible authentication solution for Rails however nobody said that implementing it on my project was going to be an easy task. I started by installing the devise gem and creating a devise user model, apparently that's all I needed in order to make things work however the requests from my React application weren't hitting the right controller, or at least that's what I thought, since I thought that my user controller was still responsible for signing up new users. Little did I know that Devise implements a custom Registration controller for that purpose, after several days tryinging to find out what was the best way to set that up, I figured out a way to make things work for my project:

```
class RegistrationsController < Devise::RegistrationsController

    skip_before_action :verify_authenticity_token, :only => :create
# register a new user
    def create
      @user = User.new(user_params)
      if @user.save
        binding.pry
        sign_in :user, @user
        # session[:user_id] = @user.id
        render :json=> @user, :status=>200
        binding.pry
      else
# devise custom error
    binding.pry
        warden.custom_failure!
        render json: { error: 'signup error' }, status: :unprocessable_entity
      end
    end

# update user details
    def update
      @user = User.find_by_email(user_params[:email])
  
      if @user.update_attributes(user_params)
        render json: @user
      else
        warden.custom_failure!
        render :json=> @user.errors, :status=>422
      end
   end

# remove a user
    def destroy
      @user = User.find_by_email(user_params[:email])
      if @user.destroy
        render :json=> { success: 'user was successfully deleted' }, :status=>201
      else
        render :json=> { error: 'user could not be deleted' }, :status=>422
      end
    end
  
    private
  
    def user_params
       params.require(:user).permit(:email, :password, :password_confirmation)
    end
  end
```

Turns out that I needed to create my own Registration controller, which inherited Devise::RegistrationsController, if I wanted to be able to use Pry in order to find out where my requests where landing. What was also crucial for this solution to work was to have this piece of code on my Application controller, so that Devise can sanitize the params hash:

```
class ApplicationController < ActionController::Base
    # skip_before_action :verify_authenticity_token
    before_action :configure_permitted_parameters, if: :devise_controller?
    protect_from_forgery with: :exception, prepend: true

    protected

    def configure_permitted_parameters
        devise_parameter_sanitizer.permit(:sign_up, keys: [:user => [:email, :password, :password_confirmation]])
      end
end
```

This setup is currently working for me with no issues and now my next challenge is to implement Omniauth on top of it.
