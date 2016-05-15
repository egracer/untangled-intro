# Model-View-Controller Architecture

This is a very basic and crucial concept to understand. An application's code is best separated into three logical
sections.

- Model: How the application's data is stored by the computer.
- View: How the application displays data to the user.
- Controller:
    1. How the application takes data from the model and provides it to the view.
    2. How the application takes data from the view and provides it to the model.

There are several reasons for adopting this architecture:

- By separating view concerns from model concerns, you can completely change your UI without needing to change the
implementation of your data storage. Similarly, you can completely change the implementation of your data storage
without needing to rewrite your UI.
- You can write multiple views for the same model.
- You can access multiple models from the same view.

### Example: Responsive web design
For example, you could write a mobile, tablet, and desktop UI that all access the same data from a remote server.

### Example: Website Authentication


## Additional Materials

- [Understanding Model-View-Controller](http://blog.codinghorror.com/understanding-model-view-controller/) is a concise
description, with examples, of how MVC architecture works.
- The [iOS Developer Library](https://developer.apple.com/library/ios/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html)
has a nice diagram of the interactions between model, view, and controller.