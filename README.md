:warning: <em> All of my projects are a WIP! They are experiments and are not a final version (and probably will never be!). </em>

<div align="center">

<br />

  <h3 align="center">Intelligent Blog Web Application</h3>

  <p align="center">
     ·
    <!-- LINK TO SECTION ON THE PAGE WITH SCREENSHOTS OF HOW IT WORKS -->
    <a href="#how-it-works">Show Me How To Use It!</a>
    ·
  </p>
  
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#functionality">Functionality</a></li>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
        <li><a href="#running-the-app">Running The App</a></li>
      </ul>
    </li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
    <li><a href="#how-it-works">How It Works</a></li>
  </ol>
</details>

<br />

<!-- ABOUT THE PROJECT -->
## About The Project

### Functionality

* Simple (but intelligent) web application to publish blog posts. Some features:
  * a rich text editor (**Action Text**),
  * an interaction area with **OpenAI Chat API** for the user to get suggested content when creating a new blog post (but this hasn't been pushed to production yet!).
  
* The user can set `Published at` dropdown fields when creating a blog post to define whether it will be
  * published (i.e. already visible to other users),
  * scheduled to be published at a later date, or
  * saved as a draft.
  
* The user(s) or blog administrator is defined at the time of application start up (more on that in "Getting Started").
* The `Sign In` page can only be accessed with the URL, given it should only be acessible by the administrator of the blog.
* The administrator can edit their email address and password once signed in.

### Built With

* This is a **Ruby on Rails** web application with a **PostGreSQL** database. It uses **TailwindCSS** for styling. The storage of cover images is handled as follows:
  
  * Active Storage (i.e. saved to local disk) in development.
    
  * An **Amazon S3** Object Storage bucket in production. The setting up of this bucket or the database for production won't be covered here. You can find a live demo of the app using Amazon's storage service at the bottom of the page (and you can change `config.active_storage.service = :amazon` to `:local` in `production.rb` if you clone this).

  <br />

* ![PostGreSQL]
* ![AWS]
* ![Ruby]
* ![Ruby on Rails]
* ![TailwindCSS]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

  * Make sure you have the following installed:
    * Ruby, check with `ruby -v` on the command line. Otherwise, install it [here](https://www.ruby-lang.org/en/documentation/installation/).
    * Ruby on Rails, check with `rails -v` on the command line. Get started with [Ruby on Rails](https://guides.rubyonrails.org/getting_started.html).
    * PostGreSQL, check with `postgresql -v` on the command line. Otherwise, follow instructions according to your operating system.
   
  * If you plan on using the AI feature, you will need to generate an [OpenAI API key](https://platform.openai.com/api-keys).


### Installation

  * Clone this repository: `git clone https://github.com/aliciademorauk/intelligent_blog`.

  * Navigate to the repository: `cd intelligent_blog`.
    
  * Run `bundle install` to install all the Ruby gems.
    
  * Remove config/master.key and config/credentials.yml.enc. Run `EDITOR=vim rails credentials:edit` in the terminal to create a new `master.key` and `credentials.yml.enc`. Use this file to store API keys.
    
  * Go to `seeds.rb` file and write your email next to `email=` to specify the email that you, as the administrator, will use to sign into the blog app.
    

### Running the App
    
  * Run `rails db:create:all` and `rails db:migrate`.
    
  *  Run `rails db:seed` to populate the database with data found in `seed_posts.JSON`. This will do two things: populate the blog with some sample posts (which you can modify in `seed_posts.JSON`) and set you up as a user.
    *  Note that **a password will be automatically generated for you and printed to the console**. You can use this to sign in the first time and then modify your password in `Edit Profile` once signed in.
 
  *  Run `bin/dev` to start the Rails server and the TailwinCSS watcher as specified in `Procfile.dev`.
    
  *  In your browser, go to `http://localhost:3000` to experience the site as a non-logged in user (i.e. read-only) or sign in at `http://localhost:3000/users/sign_in` to add and edit blog posts.

  *  To reset the application data back to the seed data, stop the program, open the rails console with `rails c` and execute the following prior to re-running the application: `User.destroy_all` and `BlogPost.destroy_all`.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [ ] Implement Devise invitable to allow users by invitation only to collaborate on the blog
- [ ] Implement 'Forgot your password?' (user has to reseed the app with a different email and redeploy the application if in production)
- [X] Use OpenAI's Chat Completions API for user to leverage text generation model to get help writing blog post

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [Best README.md Template](https://github.com/othneildrew/Best-README-Template)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


## How It Works
<p><a href="https://blogpost-webapp.onrender.com"> Click here for a live demo environment! </a></p>

<em>Note there may be a slight delay (~1 min) in completing the request to open the link given that the app is deployed under a free plan.</em>

<br />

1. The administrator goes to the `Sign In` page.
  <br />
  <img width="500" alt="Screenshot 2024-04-22 at 21 12 40" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/1bc34c61-0072-4ed1-ae87-7b26f9541c9f">
  <br />
  
2. After signing in, draft and scheduled posts come first in the home page.
  <br />
  <img width="500" alt="Screenshot 2024-04-22 at 21 04 32" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/e84ba3d1-026a-4978-b273-a41221121885">
  <img width="500" alt="Screenshot 2024-04-22 at 20 33 53" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/b6da562f-b3ae-42c4-8e08-97f27f5438ee">
  <br />
  
3. The administrator can click on a blog post to edit it or add a new blog post with the button on the navigation bar, both of which open the rich text editor.
  <br />
  <img width="500" alt="Screenshot 2024-04-22 at 20 33 26" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/cac89325-5b43-4242-8da5-c8d0d1328205">
  <img width="500" alt="Screenshot 2024-04-22 at 20 28 43" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/730d4886-0533-47b0-92ae-9d00e43e26a9">
  <br />

4. (DEVELOPMENT) If the user is creating a new blog post, the user can write down a prompt which will be sent to OpenAI's Chat API and a 250 word blog post based on that prompt, written in a playful tone of voice, will be returned.
  <br />
   <img width="500" alt="Screenshot 2024-04-24 at 17 47 46" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/b3ea87b5-5e18-46c6-b73f-105c6cb6ed78">
   <img width="500" alt="Screenshot 2024-04-24 at 17 48 40" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/33cd81eb-4dde-4b05-9b5f-66438b368bac">
  <br />

5.  (DEVELOPMENT) The user can regenerate the OpenAI's response and the contents written in the blog post's text editor won't be lost.
  <br />
   <img width="500" alt="Screenshot 2024-04-24 at 17 49 13" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/b19e8ea4-b794-4e57-838d-deee619ba4a0">
   <img width="500" alt="Screenshot 2024-04-24 at 17 49 37" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/d6cbcfc1-4e93-4995-a65e-3d6bb111e308"> 
  <br />
   
   
6. The user can modify email and password details.
  <br />
  <img width="500" alt="Screenshot 2024-04-22 at 20 34 10" src="https://github.com/aliciademorauk/BlogPost-WebApp/assets/81619741/0f9c9500-35a3-4c71-8bda-181000c7ca14">
  <br />

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[JavaScript]: https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E
[HTML]: https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white
[CSS]: https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white
[TailwindCSS]: https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white
[Ruby]: https://img.shields.io/badge/Ruby-CC342D?style=for-the-badge&logo=ruby&logoColor=white
[Ruby on Rails]: https://img.shields.io/badge/Ruby_on_Rails-CC0000?style=for-the-badge&logo=ruby-on-rails&logoColor=white
[PostGreSQL]: https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white
[AWS]: https://img.shields.io/badge/Amazon_AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white
