# Model-View-Controller Architecture

This is a very basic and crucial concept to understand. An application's code is best separated into three logical
sections.

- Model: How the application's data is stored by the computer.
- View: How the application displays data to the user.
- Controller:
    1. How the application takes data from the model and provides it to the view.
    2. How the application takes data from the view and provides it to the model.

There are several reasons for adopting this architecture, including but not limited to the following:

- By separating view concerns from model concerns, you can completely change your UI without needing to change the
implementation of your data storage. Similarly, you can completely change the implementation of your data storage
without needing to rewrite your UI.
- You can easily create and modify multiple views for the same model.
- You can easily access multiple models from the same view.

### Example: Responsive web design

People now visit websites from a wide variety of devices that use a wider variety of screen sizes and resolutions. It's
critical that websites display information in a UI best suited to the viewer's current device without sacrificing
content.

One way to accomplish this would be to have a different web page for each kind of device, and redirect the user's
browser to that device-specific site when they load the page. That decision would create a code maintenance problem,
because if I want to add some new content to my website, I now have to separately add the same content to each page.
The same thing goes for modifying and deleting content -- any change to the site has to be made once each for large,
medium, small, and mobile screens.

The above design demonstrates that the developer is fusing model and view code. The raw data on each site
is the same, but the UI is different. Since the developer has not separated the data from the UI, the model
must be repeated in code several times.

One of the reasons that modern website design calls for utilizing CSS stylesheets is to prevent this problem. A
developer only has to write one HTML page with the content, using CSS to inform the browser which view to use based on
the viewer's screen size.

The developer can change content in one place and have it propagate to all screen sizes (an example of changing the
model without changing the view). Similarly, the developer could change the layout of the application's mobile page
 without changing the actual content of the page (changing the view without changing the model).

### Example: Website Authentication

Security has been a hot topic for awhile now, and it doesn't show any signs of slowing. One way to authenticate a
web app's users is to invite them to sign in with a third-party site.

Many sites have a "Sign in with (pick your favorite company)" button, which uses that company's controller code to
access its data model in order to identify a user. That controller returns data, like your name, email, and picture, to
help set up your account on the new site.

So if a developer builds a todo list web app, that developer will have a database with each user's todo lists and todo
 items. However, the developer also has to access the third-party database to retrieve your name, picture, and email
 address when you log in.

This is a situation where the developer is using data from two models within the same view. One model is only used
briefly, for authentication and account creation. The other model is used to store the web app's proprietary data.

## Additional Materials

- [Understanding Model-View-Controller](http://blog.codinghorror.com/understanding-model-view-controller/) is a concise
description, with examples, of how MVC architecture works.
- The [iOS Developer Library](https://developer.apple.com/library/ios/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html)
has a nice diagram of the interactions between model, view, and controller.