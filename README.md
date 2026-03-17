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
``` html
* @switch(color){
   @case('red'){ ... }
   @case('green'){ ... }
   @case('yellow'){ ... }
   @default{ ... }
```
# For Loop in Template File ( HTML wali File )
* Make array in .ts file
* If array is like this
```html
  users=['sithkar','sam','sachin','satyarth','satyam']
```
```html
* @for( user of users;track user){
   <h2>{{user}}</h2>
*  }
```
* If array is like this
```html
  students=[
   {name:'sithkar',age:22,email:'sithkar@example.com'},
   {name:'sam',age:23,email:'sam@example.com'},
   {name:'sachin',age:24,email:'sachin@example.com'},
   {name:'satyarth',age:25,email:'satyarth@example.com'},
   {name:'satyam',age:26,email:'satyam@example.com'}
  ]
 ```
* Then For loop is 
```html
@for(student of students;track student){
   <h2>{{student.name}}</h2>
   <h2>{{student.age}}</h2>
   <h2>{{student.email}}</h2>
}
```
# Signals
* A signal is a wrapper around a value that give a signal when value changes.
* Eg : count = signal(10);
* **Types of Signals**
* **Writable Signals** : value can  be change
* **Computed Signals** : read  only
# Data Type with Signals
* In .ts file
```html
import { Component, signal } from '@angular/core';
@Component({
  selector: 'app-root',
  imports: [],
  templateUrl: './app.html',
  styleUrl: './app.css'
})
export class App {
* only signal ka  datatype define krna ho
 data = signal<number|string>(10);
* signal and data dono ka datatype define krna ho
 data: WritableSignal<number | string> = signal(10);
* Computed Signal (Only Read)
  count:Signal<number> = computed(()=>200);
 updateData() {
  this.data.set('Hello World');
 }
* Update : Limited use : This only work for singal data type value
updateVal(){  
  this.data.update((val))=>val+1);
}
}
```
.html file
```html
<h1>Signlas</h1>
{{data()}}
<button (click)="updateData()" >update</button>
```
# Computed Signals
* Forcefully cannot be change but if its dependency is on another signal then it can be change.
* .ts file
```html
import { Component, signal,computed } from '@angular/core';

@Component({
  selector: 'app-root',
  imports: [],
  templateUrl: './app.html',
  styleUrl: './app.css'
})
export class App {
 x = signal(10);
 y = signal(20);
 z = computed(() => this.x() + this.y());
 
 showValue(){
   console.log(this.z());
   this.x.set(100);
   console.log(this.z());
 }
 updateX(){
   this.x.set(100);
 }
}
```
* .html file
```html
<h1>Computed Signlas</h1>

<h1>{{z()}}</h1>
<button (click)="showValue()" >Show value</button>
<button (click)="updateX()" >Update value</button>
```
# Effect in Angular
* **effect** is used to run some code automatically whenever a signal value changes.
* **Effect = Automatically run code when a signal changes.**

* **Real Life Example**
  * Imagine YouTube notifications.
  * Channel uploads video → notification automatically appears.

  **Here:**
  * Signal → number of videos
  * Effect → notification system

  Whenever the signal changes → **effect runs automatically**.
*  .ts file
```html
import { Component, signal, effect } from '@angular/core';

@Component({
  selector: 'app-root',
  imports: [],
  templateUrl: './app.html',
  styleUrl: './app.css'
})
export class App {

  count = signal(0);
  displayHeading = signal(false);

  constructor(){
    effect(() => {
      if(this.count() == 2){
        this.displayHeading.set(true);

        setTimeout(() => {
          this.displayHeading.set(false);
        }, 2000);

      }else{
        this.displayHeading.set(false);
      }
    })
  }
  toggleValue(){
    this.count.set(this.count() + 1);
  }
}
```
* .html file
```html
<h1>Computed Signlas</h1>
<h1>{{count()}}</h1>
<button (click)="toggleValue()" >Update userName</button>

@if(displayHeading()){
   <h1 style="background-color: green;">Page Heading</h1>
}
```
# For Loop contextual Variables
.ts file 
* Make a Array users
.html file
```html
<h1>For Loop contextual Variables</h1>
@for(user of users;track user;
let i = $index;
let f=$first;
let l=$last;
let o=$odd;
let e=$even)
{
    @if(f||l){
        //code
    }
    @if(o){
        //code
    }
     @if(e){
        //code
        <h1>{{$count}}</h1>
    }
}
@empty(){
    <h1> No Record Found </h1>
  }
```
# Two Way Binding
**Two-way data binding in Angular** means **data flows in both directions**:

1. **Component → View (HTML)**
2. **View → Component**

So if the **value changes in the input field**, the **component variable also updates automatically**, and if the **component value changes**, the **UI updates automatically**.

**Code**
* .ts file
```html
import { Component, signal, effect } from '@angular/core';
import { FormsModule } from '@angular/forms';

@Component({
  selector: 'app-root',
  imports: [FormsModule],
  templateUrl: './app.html',
  styleUrl: './app.css'
})
export class App {
   name="sithkar"
}
```
* .html file
```html
<h1>Two Way Binding</h1>
<input [(ngModel)]="name" type="text" placeholder="enter name">

<h1>{{name}}</h1>
```
* **Exercise : Make To-Do List**
# Dynamic Style
* .ts file
```html
import { Component, signal, effect } from '@angular/core';
import { FormsModule } from '@angular/forms';

@Component({
  selector: 'app-root',
  imports: [FormsModule],
  templateUrl: './app.html',
  styleUrl: './app.css'
})
export class App {
   bgColor="red";
   fontSize=80;
    headingSizeBig="80px";
    headingSizeSmall="30px";
    zoom=true;
    updateHeadingSize(){
      this.zoom=!this.zoom;
    }
}
```
* .html file
```html
<h1
[style.backgroundColor]="bgColor"
[style.fontSize.px]="fontSize"
>Dynamic Style</h1>

<h1 [style.fontSize]="zoom ? headingSizeBig:headingSizeSmall" >Heading</h1>
<button (click)="updateHeadingSize()">Toggle Font</button>
<h1 [style.fontSize]="zoom ? '80px':'50px'" >Hii</h1>
```
## Angular Directives
### 1. Component Directives
- The most common type of directive.
- Used with a component's template to define UI.
- Every Angular component itself is a directive with a template.
---
### 2. Structural Directives
- Used to change the structure of the DOM.
- They can **add, remove, or manipulate elements** in the DOM.
- Common examples: `*ngIf`, `*ngFor`
---
### 3. Attribute Directives
- Used to modify the **appearance or behavior** of an existing element.
- They do not change the DOM structure.
- Common examples: `ngClass`, `ngStyle`
   






  









