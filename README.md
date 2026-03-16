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
* **Type of Component** : 1. Normal Component  2. Inline Component
# Make Custom Component
* import { Component } from '@angular/core';
* @Component({    
    selector: 'app-profile',
    template:`<h1>Profile</h1>`,
    styles:'h1{color:blue; }'
})
* export class Profile { }
# Function Call on Button Click
* <button (click)="handleClick()" >Touch me</button>
* Define handleClick() function in .ts file
* To call function inside a function use this.function_Name
# Define Data Type in Angular
* Syntax : var_name:data_type = value
* For Multiple Value : data:string | nummber = "Sithkar"
* For Any data type : other:any = true
# Make a Counter App 
* Do it by yourself
# Important Event in Angular
* **Event** : To perform any action
* Eg : click, mouseenter,mouseleave,input,focus,blur
# Get and Set Input field Value
* **Get** : Input Field k value ko nikaalna
* **Set** : Button or External Event k upper Input field k value ko change krna
* use Template Reference Variable
* **<input type="text" value="{{email}}" placehlder="Enter Email" #emailField>**
# Style Option
* **Global Style** : Write CSS in style.css file
* Global file is attached in angular.json.
* last attached CSS file property is applicable.
# If Else in Angular | Hide-Show | Toggle
* @if(x==10) {...}
* @else {...}
# Else If Condition | Control Flow Statment
* @if(x==2) {...}
* @else if(x<2) {...}
* @else {...}
# Switch Case in Angular

  









