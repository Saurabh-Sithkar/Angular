# Angular
Angular Learning Guide
# Setup and Installation Guide
* 1st Install Node.js and npm (If you install Node, then npm gets installed along with it)
* Open Command line : write : npm i -g @angular/cli (g means globally)
* On Command line : Change folder and Go to desktop folder : run : ng new fileName
* Open this file in VS Code write : Code .  : on Command line
* To run Angular File : ng serve
* To run and Open in Browser : ng serve --open
* To check all Installation : on Command Line : run : ng version
# File Structure
 **Dependencies vs DevDependencies**
* Dependencies are the packages required to run your application in production. If you deploy your app, these packages must be installed. And DevDependencies packages are only needed during development, not when the app runs in production.
# Interpolation in Angular
* Display data from TS to HTML file
* Execuet JS code in HTML file
* Syntax : {{title}},{{2+2}},{{'hello'.toUpperCase()}},{{3==3}}
* Limitation : {{}} not declate variable inside this , not increment/decrement
# Angular CLI
* Angular CLI(Command Line Interface) is a  tool that helps developers create, build,test and deploy Angular applications.
* To Check Angular CLI Installation  : ng version
* To generate Componenet : ng generate component login  **or** ng g c login
* To get help : ng help
# Components in Angular
* In Angular, a component is the basic building block of a UI.
* **How to use one component into another component** : 
  If you want to use the Login component inside the App component, first add the Login component’s selector in app.html, and then import the LoginComponent in app.ts.
* **To generate component** : ng g c componentName


