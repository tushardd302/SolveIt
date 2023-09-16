<p align="center">
  <img src="_git%20assets/cover.png" width="600" align="center"/>
</p>

> KLiK is a PHP based Information Pool System (or simply a Social Media Website), consisting of a complete Login/Registration system, User Profile system, Chat room, Forum system and Blog/Polls/Event Management System.



## Features

* [Application Dashboard](#application-Dashboard)
* [Login/Registration and User Authentication](#Login-Registration-and-User-Authentication)
* [User Profile System](#user-profile-system)
* [Inbox/Chat room](#chatroom-inbox)
* [Forum system](#management-systems)
* [Blog Management system](#management-systems)
* [Poll/Voting Management system](#management-systems)
* [Events Management System](#management-systems)
* [Security](#security)


## Components

#### Languages
```
PHP 5.6.40
SQL 14.0
JavaScript ES 6
HTML5
CSS3
```

#### Database
```
MySQL Database 8.0.13
```

#### DBMS
```
phpMyAdmin 4.8.3
```

#### API
```
MySQLi APIs
```

#### Frameworks and Libraries
```
JQuery v3.3.1
BootStrap v4.2.1
```

#### Techniques
```
AJAX
```



## Details

> Details of important Features of the Application

### Application Dashboard

<p align='center'>
  <img src="_git%20assets/dashboard.png" width="500" align="center"/>
</p>

The Dashboard provides a central interface to most features of the application. The `User profile card` on the upper left corner of the screen provides a profile summary, as well as a link to the profile and the profile-editing page. The creator button on the upper right corner provides a prominent link to the Team page, which showcases the `KLiK Creators`.

The 4 tab interface in the center provides access to `latest`, or most recently created `Forums`, `Blogs`, `Polls` and `Events`. The components show the individual characteristics of the respective elements, like total `upvotes` for a forum, `likes` for a blog, `votes` for a poll and `days remaining` for events. There are 2 more buttons, which go to the `KLiK Forums` (the central interface for the Forums) and the `KLiK Hub` (The central interface for the Blog, Poll and Event Management System).


### Login/Registration and User Authentication

<p>
  <img src="_git%20assets/login.png" width="400" align="right"/>
</p>

KLiK supports a complete login/registration and User Profile system. On startup, the application shows options for logging in, signing up or contacting the website admin via email. Each user can make a unique username which cannot be changed later. The user `passwords` are `hashed` before storing in database so even admins do not have access to the original passwords as well. Additional User information include `Full Name`, `email`, `Profile Image`, `Profile Headline`, `Gender` and `Bio`.

There is also a secure `Password Recovery System` which enables user to reset their passwords in a secure way. The app generates temporary encrypted token-links with a certain expiry time which when used by user prompts to change the password. Since that also requires current password, the process is secure and has lesser chances of exploitation.

The app uses several authentication methods for signing up and logging in. It checks for `empty fields`, `wrong username`, `wrong password`, `SQL errors`, `server errors` and in case of signing up, `corrupted image` or `wrong image type` errors

### User Profile System

<p>
  <img src="_git%20assets/profile.png" width="350" align="left"/>
</p>

KLiK has a complete `User profile system`. Each user is assigned a profile on signing up, with which the user can create Forums, Blogs, Events etc and interact with the app's features. The user's full name, headline and bio, as well as profile image are optional, meaning that anyone can signup without setting those. In that case, the user will be assigned a default user image and the headline, bio and full name will be empty.

The `user profile` can be accessed through the option in the settings menu on the navigation bar, or more simply, by clicking the user image on the user profile card, which is present on the top left corner of the app screen on most pages. The profile page shows the basic User information like username, full name, gender, headline and bio. Apart from that, it shows the different `Forums` and `Blogs` the User has created along with the `Polls` he/she has participated in. If in case the user has not done any of that or is new, the page shows a cute little bongo cat with a 'such empty' caption to remind you that you need to be more active :)

There is also a `Profile Editing System` which allows the User to edit his profile information. It can be accessed through the respective option in the settings menu in the navigation bar or by simply clicking the pencil icon next to the user profile image on the profile card. The system allows the user to change most of his information except for the username, which cannot be changed. All fields already have the current information, so the user does not have to type everything all over again if he only wishes to slightly edit the current information. The password can also be changed, however, only by providing the current password to retain a more secure interface.

### ChatRoom / Inbox

<p align="center">
  <img src="_git%20assets/inbox.png" width="600" align="center"/>
</p>

KLiK also has a chatbox, which uses `PHP` & `AJAX` for real-time chatting with other users. The section on the left is a list of all the users currently on the website, while the right chat screen is for displaying the ingoing and outgoing messages. A user can access a chat with a certain user by clicking on him/her in the users list, which will retrieve all the chat messages from the database. The ingoing and outgoing messages are styled differently in order to maintain readability. Chatting is done in real-time, without the need to refresh the page continuously.

**Possible Improvements**:
* `optimization`: All messages of a chat are retrieved at once, and this can cause delays if the chat is big. This can be fixed by implementing incremental load of messages to load only the messages being displayed on-screen.
* `user search`: A search feature can be implemented in the user list to directly search for a particular user, thus saving time.

### Security

* `Password hashing` before storing in database.
* Password Reset done through individually created `encrypted tokens` sent via email as a form of a link. The tokens have a certain expiry date after which they cannot be used.
* Filtering of information obtained from `$_GET` and `$_POST` methods to prevent `header injection`.
* Implementation of `MySQLi Prepared Statements` for **advanced** database security.

  **Example:**
```php
$sql = "select uidUsers from users where uidUsers=?;";
        $stmt = mysqli_stmt_init($conn);
        if (!mysqli_stmt_prepare($stmt, $sql))
        {
            header("Location: ../signup.php?error=sqlerror");
            exit();
        }
        else
        {
            mysqli_stmt_bind_param($stmt, "s", $userName);
            mysqli_stmt_execute($stmt);
            mysqli_stmt_store_result($stmt);
       }
```



