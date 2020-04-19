---
layout: post
title:      "Designing a UI with Bootstrap Studio"
date:       2020-04-19 19:05:05 +0000
permalink:  designing_a_ui_with_bootstrap_studio
---

The legend Avi Flombaum once said during one of his lectures that the most intimidating moment for a developer is when they see a blank screen and don't know where to start to develop an app. I could say that I've been there and done that many times specially when building frontend users interfaces.

My standard was to build a top-class and mobile-first UI for my application but it's easier said than done. Typically when I'm coding in HTML and CSS I find it hard to keep track of the changes I'm implementing and how they affect the application I'm building since I need to be constantly saving my changes and refresh my browser in order to see the updated version of my code and also you need to have both VS code and Chrome open at the same time. Also I'm not very familiar with all the different Bootstrap classes yet since there's quite a few, Bootstrap is a free and open-source CSS framework directed at responsive, mobile-first front-end web development in case you haven't heard about it before.

For all of the reasons stated above and since the goal here is to build a user-centric killer UI, I decided to get a Bootstrap Studio license. If we use gems and code built by other developers for Ruby, why not do the same for HTML, CSS and even Javascript. Bootstrap Studio is a web design application. It offers a large number of components for building responsive pages including headers, footers, galleries and slideshows along with basic elements such as spans and divs.
You can use Bootstrap for free but if you are creating a webpage with Bootstrap studio you need either need to get a standard license ($29 dollars with 1 year of free upgrades) or a lifetime license which costs $60 but you get free upgrades forever. I went for the first option just to give it a try, and so far so good. I can now see all my HTML and CSS code in one place and I'm learning loads about Bootstrap thanks to this platform. All in all I think it's been a valuable investment as I've managed to create an elegant and responsive page in just a day, here's the code:


```
<html><head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=no">
    <title>NightClub page</title>
    <link rel="stylesheet" href="assets/bootstrap/css/bootstrap.min.css">
    <link rel="stylesheet" href="assets/fonts/ionicons.min.css">
    <link rel="stylesheet" href="assets/css/Footer-Dark.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.2/animate.min.css">
    <link rel="stylesheet" href="assets/css/styles.css">
    <link rel="stylesheet" href="assets/css/untitled-1.css">
    <link rel="stylesheet" href="assets/css/untitled.css">
</head>

<body class="nighclub-page-background-color">
    <div class="carousel slide carousel-fade nightclub-page-carousel pointer-event" data-ride="carousel" id="carousel-1">
        <div class="carousel-inner" role="listbox">
            <div class="carousel-item carousel-item-next carousel-item-left"><img class="img-fluid w-100 d-block" src="assets/img/Mayaclubbio.jpg" alt="Slide Image"></div>
            <div class="carousel-item"><img class="w-100 d-block" src="https://cdn.bootstrapstudio.io/placeholders/1400x800.png" alt="Slide Image"></div>
            <div class="carousel-item active carousel-item-left"><img class="w-100 d-block" src="https://cdn.bootstrapstudio.io/placeholders/1400x800.png" alt="Slide Image"></div>
        </div>
        <div><a class="carousel-control-prev" href="#carousel-1" role="button" data-slide="prev"><span class="carousel-control-prev-icon"></span><span class="sr-only">Previous</span></a><a class="carousel-control-next" href="#carousel-1" role="button" data-slide="next"><span class="carousel-control-next-icon"></span><span class="sr-only">Next</span></a></div>
        <ol class="carousel-indicators">
            <li data-target="#carousel-1" data-slide-to="0" class="active"></li>
            <li data-target="#carousel-1" data-slide-to="1" class=""></li>
            <li data-target="#carousel-1" data-slide-to="2" class=""></li>
            </ol>
    </div>
    <div class="container nighclub-page-background-color container-fluid">
        <div class="row nightclub-page-section">
            <div class="col-sm-12 col-lg-8 col-xl-8 d-flex justify-content-center align-content-center justify-content-md-center justify-content-lg-end justify-content-xl-end ratings-and-reviews">
                <aside class="border rounded shadow-sm ratings-and-reviews-component" data-bs-hover-animate="pulse"></aside>
            </div>
            <div class="col-12 col-sm-12 col-lg-4 col-xl-4 d-flex justify-content-center justify-content-lg-start justify-content-xl-start location-section">
                <aside class="border rounded shadow-sm location-component animated pulse" data-bs-hover-animate="pulse"></aside>
            </div>
            <div class="col-sm-12 col-lg-8 col-xl-8 d-flex flex-column justify-content-center align-items-center align-items-sm-center justify-content-md-center justify-content-lg-end align-items-lg-end justify-content-xl-end align-items-xl-end details-and-amenities-section">
                <aside class="border rounded shadow-sm mb-auto details-component" data-bs-hover-animate="pulse"></aside>
                <aside class="border rounded shadow-sm d-flex reviews-component" data-bs-hover-animate="pulse"></aside>
            </div>
            <div class="col-sm-12 col-lg-4 col-xl-4 d-flex justify-content-center order-sm-1 justify-content-lg-start ml-lg-auto justify-content-xl-start ml-xl-auto nearby-section">
                <aside class="border rounded shadow-sm map-component" data-bs-hover-animate="pulse"></aside>
            </div>
        </div>
    </div>
    <div class="footer-dark">
        <footer>
            <div class="container">
                <div class="row">
                    <div class="col-sm-6 col-md-3 item">
                        <h3>Services</h3>
                        <ul>
                            <li><a href="#">Web design</a></li>
                            <li><a href="#">Development</a></li>
                            <li><a href="#">Hosting</a></li>
                        </ul>
                    </div>
                    <div class="col-sm-6 col-md-3 item">
                        <h3>About</h3>
                        <ul>
                            <li><a href="#">Company</a></li>
                            <li><a href="#">Team</a></li>
                            <li><a href="#">Careers</a></li>
                        </ul>
                    </div>
                    <div class="col-md-6 item text">
                        <h3>Company Name</h3>
                        <p>Praesent sed lobortis mi. Suspendisse vel placerat ligula. Vivamus ac sem lacus. Ut vehicula rhoncus elementum. Etiam quis tristique lectus. Aliquam in arcu eget velit pulvinar dictum vel in justo.</p>
                    </div>
                    <div class="col item social"><a href="#"><i class="icon ion-social-facebook"></i></a><a href="#"><i class="icon ion-social-twitter"></i></a><a href="#"><i class="icon ion-social-snapchat"></i></a><a href="#"><i class="icon ion-social-instagram"></i></a></div>
                </div>
                <p class="copyright">Company Name © 2017</p>
            </div>
        </footer>
    </div>
    <script src="assets/js/jquery.min.js"></script>
    <script src="assets/bootstrap/js/bootstrap.min.js"></script>
    <script src="assets/js/bs-init.js"></script>


</body></html>
```


As you can see the code looks pretty clean and once the you add the bootstrap CSS classes to it, the results are great!

