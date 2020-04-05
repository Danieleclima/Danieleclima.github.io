---
layout: post
title:      "Omniauth with Devise and Redux"
date:       2020-04-05 20:34:55 +0000
permalink:  omniauth_with_devise_and_redux
---


Not long ago, I did read that Devise is not precisely a walk in the park and the truth is that I couldn't agree more with that statement, specially if you are working with a Redux frontend. Setting up Devise user authentication was relatively easy, I had some trouble at the begining since even though the fictitous users I created were getting authenticated and persisted, my controllers weren't storing any cookies on the client. The fix to this issue was relatively easy, all I had to do was updating my session_store initializer so that It could set cookies during development, notice the first line on the following statement:

```
if Rails.env === "production" || "development"
Rails.application.config.session_store :cookie_store, key: "_authentication_app", domain: "http://localhost:3001"
else
    Rails.application.config.session_store :cookie_store, key: "_authentication_app"
end
```

Done! Creating users through a 3rd party Oauth provider, however, is a different story. In the sense that the request sent from the client goes through redirects and that makes it quite complicated for your API and Frontend to communicate, my user action ilustrates the problem:

```
export const createUser = user => {
    return (dispatch) => {
        if (user) {
            dispatch({ type: 'START_CREATING_USER' });
            let targetUrl = `http://localhost:3001/users`;
            // Post the user to the Rails API user controller
            fetch(targetUrl, options("POST", { user: user }))
                // returning user from the Rails API
                .then(u => {
                    debugger
                    return u.json()
                })
                .then(current_user => {
                    console.log('c')
                    debugger
                    // sending the returned user to the Redux userReducer
                    dispatch({ type: 'CREATE_USER', user: current_user })
                })
        }
    }
}
```

The above Redux action is pretty straight forward, it receives a user that's being passed from a form, and then sends a post request to the API which then returns the user and finally that same users gets saved on my Redux store so that it is accesible from all my components. that's the same logic I wanted to apply when creating Omniauth users however, due to the reason I mentioned earlier, that was a no-go. Instead, what my gut is suggesting me to do at the moment is simply create the new user on my `OmniauthCallbacksController < Devise::OmniauthCallbacksController` controller and then send a redirect response to the client, I'm under the impression that something along these lines might work:

```
render json: {"redirect":true,"redirect_url": apps_path}, status:200
```

If that does it, then all I have to do check the login status when my components render again. I have already created a Redux action for that:

```
export const checkLoginStatus = () => {
    debugger
    return (dispatch) => {
        dispatch({ type: 'START_CHECKING' });
        fetch(`http://localhost:3001/logged_in`, {
            method: "GET",
            headers: {
                'Content-Type': "application/json",
                Accept: "application/json"
            },
            credentials: 'include'
        })
            .then(user => {
                return user.json()
            })
            .then(current_user => {
                debugger
                dispatch({ type: 'ADD_LOGGED_IN_USER', user: current_user })
            })
            .catch(error => {
                debugger
                console.log(error)
            })

    }
}
```

Wish me luck!
