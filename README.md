# Hillcrest React Developer Volunteer

## Introduction

This is my initial edit of the Hillcrest-React page. Stay tuned for more information, as well as screenshots and code snippets.

One of the projects I am currently working on is the website of a Portland church called Hillcrest. The purpose of this project is to create a responsive one-page React application. Since I am currently the sole developer, I have the unique opportunity to plan out my own process and thus far I have completed several [front end tasks](#front-end-tasks) and [back end tasks](#back-end-tasks). In the near future, I will work on updating Hillcrest's website for the parts of administration who are not technically savvy and want to easily manage what displays in their website.

## Front End Tasks

* [Navbar](#navbar)
* [Front Page](#front-page)
* [Footer](#footer)

### Navbar

My task was to create a hamburger menu for mobile screens that responsively expands to a navigation bar for larger screen sizes. 

#### Screenshot of the Navbar on a mobile display:

![Navbar Mobile](https://github.com/mdarlow/Hillcrest-React/blob/main/Navbar/Navbar-Mobile.jpg)

#### Screenshot of the open menu:

![Navbar Mobile Open](https://github.com/mdarlow/Hillcrest-React/blob/main/Navbar/Navbar-Mobile-Open.jpg)

#### Screenshot of the page on a larger screen:

![Navbar Tablet](https://github.com/mdarlow/Hillcrest-React/blob/main/Navbar/Navbar-Tablet.jpg)

#### This is my code for the Navbar functions:

    function openNav() {
        document.getElementById("Navbar").style.width = "40%";
    }
    
    function closeNav() {
        document.getElementById("Navbar").style.width = "0";
    }

#### The following code is for automatically taking the user to the top of the screen each time a page link is selected. The scroll location would otherwise stay saved even after transitioning. This creates the appearance of multiple pages in a single-page application.

    function scrollToTop() {
        window.scrollTo(0, 0)
    }

#### Navbar.js code:

    function Navbar() {
        return (
            <div>
                <div className='Navbar-social-media-buttons'>
                    <SocialIcon network="youtube" style={{ height: 35, width: 35 }} target='_blank' url="https://www.youtube.com/channel/UCDlqz_OdJ2Owl00GAOsTbzw/videos" />
                    <SocialIcon network="twitter" style={{ height: 35, width: 35 }} target='_blank' url="https://twitter.com/HillcrestBible" />
                    <SocialIcon network="facebook" style={{ height: 35, width: 35 }} target='_blank' url="https://www.facebook.com/HillcrestBibleChurch/" />
                </div>
                <div id="Navbar" class="sidebar">
                    <a href="javascript:void(0)" class="closebtn" onClick={closeNav}>x</a>
                    <Link to="/home" onClick={scrollToTop}>Home</Link>
                    <Link to="/about" onClick={scrollToTop}>About Us</Link>
                    <Link to="/sermons" onClick={scrollToTop}>Sermons</Link>
                    <Link to="/prayer" onClick={scrollToTop}>Request Prayer</Link>
                </div>
                <div class="hamburgerClass" id="hamburger">
                    <button class="openbtn" onClick={openNav}>☰</button>
                </div>
            </div>
        )
    }

#### Navbar's CSS code:

    /****************************************************/
    /******* Social Media buttons - fixed on side *******/
    .Navbar-social-media-buttons {
        display: none;
    }
    .Navbar-social-media-buttons a {
        display: none;
    }
    /******* Social Media buttons - fixed on side *******/
    /****************************************************/


    /***************************************************************/
    /************************* Navbar Main *************************/
    .sidebar {
        height: 100%;
        width: 0;
        position: fixed;
        z-index: 3;
        top: 0;
        right: 0;
        background-color: #111;
        overflow-x: hidden;
        transition: 0.5s;
        padding-top: 60px;
    }
    .sidebar a {
        padding: 8px 8px 8px 32px;
        text-decoration: none;
        font-size: 25px;
        color: #818181;
        display: block;
        transition: 0.3s;
    }
    .sidebar a:hover {
        color: #f1f1f1;
    }
    .sidebar .closebtn {
        position: absolute;
        top: 0;
        right: 25px;
        font-size: 36px;
        margin-left: 50px;
    }
    
    .openbtn {
        font-size: 65px;
        cursor: pointer;
        background-color: #072035;
        color: white;
        padding: 6px 19px;
        border: none;
        border-radius: 20px;
        -webkit-transition-duration: 0.3s;
        transition-duration: 0.3s;
    }
    .openbtn:hover {
        background-color: rgb(0, 0, 110);
        -webkit-transition-duration: 0.3s;
        transition-duration: 0.3s;
    }

    .hamburgerClass {
        position: fixed;
        top: 1px;
        right: 1px;
        z-index: 2;
    }
    #main {
        transition: margin-right .5s;
        padding: 16px;
    }
    /************************* Navbar Main *************************/
    /***************************************************************/


    /***************************************************************/
    /******************* Screens 800px and above *******************/
    @media only screen and (min-width: 800px) {
        .openbtn {
            display: none;
        }
        .sidebar {
            height: auto;
            width: auto;
            position: fixed;
            z-index: 3;
            top: 50px;
            left: 35%;
            background-color: #072035;
            overflow-x: visible;
            transition: 0.5s;
            padding-top: 0px;
        }
        .sidebar a {
            padding: 8px 8px 8px 30px;
            text-decoration: none;
            font-size: 20px;
            color: #818181;
            display: inline-block;
            transition: 0.3s;
        }
        .sidebar .closebtn {display: none;}
    }
    @media only screen and (min-width: 1000px) {
        .openbtn {
            display: none;
        }
        .sidebar {
            height: auto;
            width: auto;
            position: fixed;
            z-index: 3;
            top: 50px;
            left: 35%;
            background-color: #072035;
            overflow-x: visible;
            transition: 0.5s;
            padding-top: 0px;
        }
        .sidebar a {
            padding: 8px 8px 8px 32px;
            text-decoration: none;
            font-size: 25px;
            color: #818181;
            display: inline-block;
            transition: 0.3s;
        }
        .sidebar .closebtn {display: none;}
    }
    @media only screen and (min-width: 1200px) {
        .openbtn {
            display: none;
        }
        .sidebar {
            height: auto;
            width: 50%;
            position: fixed;
            z-index: 3;
            top: 50px;
            margin: auto;
            max-width: 1200px;
            left: 0;
            right: 0;
            margin-left: auto;
            margin-right: auto;
            background-color: #072035;
            overflow-x: visible;
            transition: 0.5s;
            padding-top: 0px;
            text-align: center;
        }
        .sidebar a {
            padding: 8px 8px 8px 32px;
            text-decoration: none;
            font-size: 25px;
            color: #818181;
            display: inline-block;
            transition: 0.3s;
        }
        .sidebar .closebtn {display: none;}
    }
    @media only screen and (min-width: 1315px) {
        .Navbar-social-media-buttons {
            display: unset;
            position: fixed;
            top: 30%;
            left: 1vw;
            width: 0;
            word-wrap: break-word;
        }
        .Navbar-social-media-buttons a {
            display: unset;
            margin-top: 1px;
            filter: grayscale(15%) opacity(30%);
        }
    }
    @media only screen and (min-width: 1755px) {
        .openbtn {
            display: none;
        }
        .sidebar {
            height: auto;
            width: auto;
            position: fixed;
            z-index: 3;
            top: 50px;
            margin: auto;
            max-width: 1200px;
            left: 0;
            right: 0;
            margin-left: auto;
            margin-right: auto;
            background-color: #072035;
            overflow-x: visible;
            transition: 0.5s;
            padding-top: 0px;
            text-align: center;
        }
        .sidebar a {
            padding: 8px 8px 8px 32px;
            text-decoration: none;
            font-size: 25px;
            color: #818181;
            display: inline-block;
            transition: 0.3s;
        }
        .sidebar .closebtn {display: none;}
    }
    /******************* Screens 800px and above *******************/
    /***************************************************************/


    /***************************************************************/
    /******************* Screens 505px and below *******************/
    @media only screen and (max-width: 505px) {
        .sidebar a {font-size: 20px;}
    }
    @media only screen and (max-width: 425px) {
        .sidebar a {font-size: 12px;}
    }
    @media only screen and (max-width: 400px) {
        .openbtn {
            font-size: 33px;
            padding: 4px 10px;
            border-radius: 10px;
        }
    }
    /******************* Screens 505px and below *******************/
    /***************************************************************/

### Front Page

My task was to create a basic front page layout that responds to the size of the user's screen. 

#### Screenshot of the Front Page on a mobile display:

![Front Page Mobile](https://github.com/mdarlow/Hillcrest-React/blob/main/Front-Page/Front-Page-Mobile.jpg)

#### Screenshots of the Front Page on a large desktop screen:

![Front Page Desktop](https://github.com/mdarlow/Hillcrest-React/blob/main/Front-Page/Front-Page-Desktop.jpg)

![Front Page Desktop](https://github.com/mdarlow/Hillcrest-React/blob/main/Front-Page/Front-Page-Desktop2.jpg)

#### FrontPage.js code:

    function FrontPage() {
        return (
            <div>
                <div className="FrontImage-Container">
                    <img className="FrontImage"
                        src={`${process.env.PUBLIC_URL}images/HillcrestExterior.jpg`}
                        alt="Exterior of Hillcrest"
                    />
                    <div className='FrontImageTitle'>
                        <h1>For where two or three gather in my name, <br />there am I with them.</h1>
                        <h3>Matthew 18:20</h3>
                    </div>
                </div>
                <div className="FrontIntro">
                    <div className="FrontIntro-columns">
                        <h1 className="NewHere">NEW HERE?</h1>
                        <Link to="/about" onClick={scrollToTop}>Get to know Hillcrest</Link>
                    </div>
                    <hr className="hr-1"/>
                    <div className="FrontIntro-columns">
                        <h1>JOIN US IN PERSON</h1>
                        <h3>Sundays at 9:40am</h3>
                    </div>
                    <hr className="hr-1"/>
                    <div className="FrontIntro-columns">
                        <h1>WATCH WITH US ONLINE</h1>
                        <h3><a href="https://www.youtube.com/channel/UCDlqz_OdJ2Owl00GAOsTbzw/videos">Next stream this Sunday at 9:40am</a></h3>
                    </div>
                </div>
                <img className="front-container"
                        src={`${process.env.PUBLIC_URL}images/GospelOfMark.jpg`}
                        alt="Gospel of Mark study"
                />
                <div className='news-events'>
                    <hr className='hr-2'/>
                    <h1>News and Events</h1>
                    <hr className='hr-2'/>
                    <div className='news-grid'>
                        <div className='news-item'>News1</div>
                        <div className='news-item'>News2</div>
                        <div className='news-item'>News3</div>
                    </div>
                </div>
            </div>
        )
    }

#### CSS Code:

    .FrontImage-Container {
        position: relative;
        margin-bottom: 10vw;
    }
    .FrontImageTitle {
        position: absolute;
        justify-content: left;
        bottom: 5.5vw;
        left: 0vw;
        font-size: 2vw;
        color: rgba(255, 255, 255, 0.75);
        background-color: rgb(122, 122, 122, .75);
        padding-left: 1vw;
        margin-bottom: -11vw;
        width: 99%;
    }
    .FrontImageTitle h3 {
        color: rgba(255, 255, 255, 0.5);
    }
    .FrontImage {
        width: 100%;
        height: auto;
        opacity: 95%;
    }
    
    .FrontIntro {
        text-align: center;
        column-count: 3;
        column-gap: 40px;
        column-rule: 1px solid #dbdbdb;
        font-size: 20px;
    }
    .FrontIntro-columns {
        text-align: center;
    }
    .FrontIntro-columns h1 {
        margin-bottom: 0px;
    }
    .FrontIntro-columns a {
        font-weight: bold;
        background-color: rgb(0, 0, 110);
        transition: .3s;
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
        border-radius: 8px;
        padding: 10px 10px;
    }

    .FrontIntro-columns a:hover {
        background-color: rgb(111, 111, 111);
        transition: .3s;
    }

    .hr-1 {
        height: 1px;
        width: 50%;
        text-align: center;
        border-width: 0;
        background-color: unset;
    }

    /*********************************************/
    /************** News and Events **************/
    .news-events h1 {
        color: #a7a7a7;
    }
    .hr-2 {
        background-color: #a7a7a7;
        height: 1px;
        width: 100%;
        text-align: center;
        border-width: 0;
    }
    .news-grid {
        width: 100%;
        display: grid;
        grid-template-columns: auto auto auto;
        background-color: white;
        padding-top: 50px;
        padding-bottom: 50px;
        column-gap: 50px;
        justify-content: space-evenly;
    }
    .news-item {
        color: white;
        background-color: rgb(0, 0, 110);
        border: 1px solid white;
        padding: 100px;
        font-size: 30px;
        text-align: center;
    }
    /************** News and Events **************/
    /*********************************************/

    .NewHere {
        position: relative;
        top: -27px;
    }
    .front-container {
        margin-top: 80px;
        margin-bottom: 80px;
        width: 100%;
        height: auto;
        opacity: 100%;
    }

    /**********************************************/
    /******************** Media *******************/
    @media only screen and (max-width: 1200px) {
        .FrontImage-Container {
            margin-bottom: 150px;
        }
        .FrontImageTitle {
            bottom: -70px;
            left: 0px;
            font-size: 24px;
            padding-left: 31.234px;
            padding-right: 0px;
            margin-bottom: 0px; 
            width: 97.4%;
        }
        .FrontIntro {
            text-align: center;
            column-count: unset;
            column-gap: unset;
            column-rule: 1px solid #dbdbdb;
        }
        .NewHere {
            position: unset;
            margin-top: -2vw;
        }
        .hr-1 {
            background-color: #dbdbdb;
        }
        .front-container {
            margin-top: 2vw;
        }
        .news-events h1 {
            font-size: 4vw;
        }
        .news-grid {
            grid-template-columns: auto auto;
            row-gap: 50px;
        }
    }
    @media only screen and (max-width: 650px) {
        .FrontIntro {
            font-size: 3vw;
        }
        .FrontIntro-columns a {
            font-size: 3vw;
        }
        .news-grid {
            width: 100%;
            display: grid;
            grid-template-columns: 75%;
            row-gap: 3vw;
        }
        .news-item {
            color: white;
            background-color: rgb(0, 0, 110);
            border: 1px solid white;
            padding: 7vw;
            font-size: 4vw;
            text-align: center;
        }
    }
    /******************** Media *******************/
    /**********************************************/

### Footer

While creating the footer, I wanted to have a sense of balance between the top and the bottom of the screen, so I added a footer image with Hillcrest's name in front of it. This is followed by a solid bar containing social media buttons.

#### Screenshot:

![Footer](https://github.com/mdarlow/Hillcrest-React/blob/main/Footer/Footer-Desktop.jpg)

#### Footer.js code:
    
    import { SocialIcon } from 'react-social-icons';
    
    
    function Footer() {
      return (
        <div className="Footer">
            <div className='Footer-Container'>
                <img className='Footer-Image'
                    src={`${process.env.PUBLIC_URL}images/HillcrestInterior1.jpg`}
                    alt="Hillcrest Church"
                />
                <div className='footer-logo-text'>
                  Hillcrest Bible Church
                </div>
            </div>
            <div className='footer-bar'>
                <div className='social-media-buttons'>
                    <SocialIcon network="youtube" style={{ height: 45, width: 45 }} target='_blank' url="https://www.youtube.com/channel/UCDlqz_OdJ2Owl00GAOsTbzw/videos" />
                    <SocialIcon network="twitter" style={{ height: 45, width: 45 }} target='_blank' url="https://twitter.com/HillcrestBible" />
                    <SocialIcon network="facebook" style={{ height: 45, width: 45 }} target='_blank' url="https://www.facebook.com/HillcrestBibleChurch/" />
                </div>
            </div>
        </div>
      )
    }

#### CSS Code:

    .Footer-Container {
        position: relative;
        text-align: center;
        margin: auto;
        margin-top: 80px;
    }
    .Footer-Image {
        width: 100%;
        height: auto;
        max-height: 500px;
        opacity: 55%;
        filter: grayscale(50%);
        object-fit: cover; /* Specifies how img should be resized to fit container */
        margin-bottom: -4px;
    }
    .footer-logo-text {
        width: 100%;
        font-size: 7vw;
        font-weight: bold;
        color: black;
        opacity: 55%;
        filter: grayscale(50%);
        position: absolute;
        top: 45%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    .footer-bar {
        margin: 0;
        height: 50px;
        width: 100%;
        background-color: #072035;
    }

    .social-media-buttons {
        text-align: center;
        width: 100%;
    }
    .footer-bar a {
         margin-left: 5px;
         margin-right: 5px;
    }

    /***************************************************************/
    /******************* Screens below 1200px **********************/
    @media only screen and (max-width: 1200px) {
        .footer-bar a {
            margin-left: 1vw;
            margin-right: 1vw;
       }
    }

    @media only screen and (max-width: 309px) {
        .social-media-buttons {
            text-align: center;
            width: 100%;
        }
    }

## Back End Tasks

* [TODO 1](#todo-1)
* [TODO 2](#todo-2)

### TODO 1

My task...

#### My code:

    TODO

### TODO 2

My task...

My code:

    TODO

*Jump to: [Page Top](#hillcrest-react-developer-volunteer), [Front End Tasks](#front-end-tasks), [Back End Tasks](#back-end-tasks)*
