# MVC

> **Model-View-Controller (MVC)** is a software design pattern that breaks an application into 3 parts: Model(the data), View(visual representation of the model) and Controller(links the model and the view).

Model
- It is the data. The model contains the business logic(that is related to the functionality of the app), state(the data about the app) and HTTP library.

View
- It is the part that is visible to the user. Essentially the view displays the application state.

Controller
- It contains the application logic and handles navigation and UI events. It is the bridge between the model and the view. The model and the view are unaware of each other, they exist independently.

Flow
- An event occurs -> the controller handles the event and dispatches the tasks to the model (fetching/changing data) and the view (updating the UI) -> the controller sends the data from the model to the view -> the view renders the data into the UI

How to implement event listeners & handlers in MVC: Publisher-Subscriber
- The events should be handled in the controller (SUBSCRIBER function in the controller)
- The events should be listened for in the view (PUBLISHER function in the view)
- Pass the subscriber function in the publisher function when the application starts. The publisher function will listen for the event and when the event happens, the subscriber function will be called as a callback.

- cf. There are many other software design patterns such as MVP and Flux. These days many developers use frameworks like React, Angular or Vue to take care of the architecture.


