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
## *ngFor Directive in Angular
`*ngFor` is a **structural directive** used to **loop through a list or array** and display data dynamically in the UI.
---
### Syntax
```html
*ngFor="let item of items"
```
* app.ts file
```html
users = ["Saurabh", "Rahul", "Aman"];
```
```html
<ul>
  <li *ngFor="let user of users">
    {{ user }}
  </li>
</ul>
```
**Nested `*ngfor`**
* app.ts file
```html
users = [
  {
    name: "Saurabh",
    skills: ["Angular", "React", "Node"]
  },
  {
    name: "Rahul",
    skills: ["Java", "Spring Boot"]
  }
];
```
* app.html
```html
<div *ngFor="let user of users">
  <h3>{{ user.name }}</h3>

  <ul>
    <li *ngFor="let skill of user.skills">
      {{ skill }}
    </li>
  </ul>
</div>
```
## *ngIf Directive in Angular
`*ngIf` is a **structural directive** used to **conditionally display or remove elements** from the DOM based on a given condition.
---
### Syntax
```html
*ngIf="condition"
```
### HTML File
```html
<!-- Basic Example -->
<h1 *ngIf="isLoggedIn">Welcome User</h1>

<!-- Using else -->
<div *ngIf="isLoggedIn; else loginBlock">
  Welcome User
</div>

<ng-template #loginBlock>
  Please Login
</ng-template>

<!-- Using then and else -->
<div *ngIf="isLoggedIn; then thenBlock; else elseBlock"></div>

<ng-template #thenBlock>
  Welcome User
</ng-template>

<ng-template #elseBlock>
  Please Login
</ng-template>
```
## *ngSwitch Directive in Angular
`*ngSwitch` is a **structural directive** used to display one element from multiple options based on a given condition.
---
### Syntax
```html
<div [ngSwitch]="expression">
  <div *ngSwitchCase="'value1'">Content 1</div>
  <div *ngSwitchCase="'value2'">Content 2</div>
  <div *ngSwitchDefault>Default Content</div>
</div>
```
# Basic Routing in Angular
* app.routes.ts file
```html
import { Routes } from '@angular/router';
import { About } from './about/about';
import { Contact} from './contact/contact';
import { Login } from './login/login';

export const routes: Routes = [
    {path:'about',component:About},
    {path:'contact',component:Contact},
    {path:'login',component:Login}
];
```
* app.ts file
```html
import { Component, signal, effect } from '@angular/core';
import { RouterLink, RouterOutlet } from '@angular/router';
@Component({
  selector: 'app-root',
  imports: [RouterLink,RouterOutlet],
  templateUrl: './app.html',
  styleUrl: './app.css'
})
export class App {
   
}
```
* app.html file
```html
<h1>Basic Routing in Angular</h1>
<ul>
    <li>
        <a routerLink="/about">About</a>
    </li>
    <li>
        <a routerLink="/contact">Contact</a>
    </li>
    <li>
        <a routerLink="/login">Login</a>
    </li>
</ul>
<router-outlet/>
```
# Header with Routing
* header.html
```html
<nav>
    <h2>Logo</h2>
    <ul>
        <li>
            <a routerLinkActive="active" [routerLinkActiveOptions]="{exact:true}" routerLink="/">Home</a>
        </li>
    <li>
        <a routerLinkActive="active" routerLink="/about">About</a>
    </li>
    <li>
        <a routerLinkActive="active" routerLink="/contact">Contact</a>
    </li>
    <li>
        <a routerLinkActive="active" routerLink="/login">Login</a>
    </li>
</ul>
</nav>
```
# 404 Page OR Page not found
* WildCard Route
```html
{ path: '**', component: PageNotFound }
```
# Pass Data from one Page to Other
* Add profile  route in app.route.ts
**Method:1**
* profile.ts file
```html
import { Component } from '@angular/core';
import { ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-profile',
  imports: [],
  templateUrl: './profile.html',
  styleUrl: './profile.css',
})
export class Profile {

  username:string|null="";
  constructor(private route:ActivatedRoute) {}
  ngOnInit() {
  this.username = this.route.snapshot.paramMap.get('name');
  console.log(this.username);
  }
}
```
* home.html file
```html
<p>Home Page</p>
<a [routerLink]="['profile',{name:'Saurabh'}]">Go to Profile</a>
```
* profile.html file
```html
<p>Welcome, {{ username }}!</p>
```
* Pass Data using button
* home.ts file
```html
import { Component } from '@angular/core';
import { Router,RouterLink } from "@angular/router";

@Component({
  selector: 'app-home',
  imports: [RouterLink],
  templateUrl: './home.html',
  styleUrl: './home.css',
})
export class Home {
constructor(private router:Router) {}

goToProfile(){
  this.router.navigate(['profile',{name:'Saurabh'}]);
}
}
```
* profile.ts file
```html
import { Component } from '@angular/core';
import { ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-profile',
  imports: [],
  templateUrl: './profile.html',
  styleUrl: './profile.css',
})
export class Profile {

  username:string|null="";
  constructor(private route:ActivatedRoute) {}
  ngOnInit() {
    this.route.paramMap.subscribe(params=>{
      this.username=params.get('name');
    })
  }
}
```
* home.html file
```html
<p>Home Page</p>
<button (click)="goToProfile()" >Go to Profile Page</button>
```
* profile.html file
```html
<p>Welcome, {{ username }}!</p>
```
# 📌 Dynamic Routing in Angular
## 🚀 Overview
Dynamic routing in Angular allows you to pass data through the URL using parameters. This helps load the same component with different data based on the route.
---
## 🔹 What is Dynamic Routing?
Instead of fixed routes like:
```
/home
/about
```
You can create dynamic routes like:
```
/profile/:name
/product/:id
```
Here, `:name` and `:id` are route parameters.
## 🔹 Step 1: Define Route
Create a route with parameters in your routing file:
```ts
import { Routes } from '@angular/router';
import { User } from './user/user';

export const routes: Routes = [
    {path:'user/:id/:name',component:User},
];
```
## 🔹 Step 2: Navigate with Parameters
### Using HTML:
```html
// home.html
<h1>User List</h1>
<ul>
    @for(user of users;track user){
        <li><a routerLink="user/{{user.id}}/{{user.name}}" >{{user.name}}</a></li>
    }
</ul>
```
### Using TypeScript:
```ts
//home.ts
import { Component } from '@angular/core';
import { Router,RouterLink } from "@angular/router";

@Component({
  selector: 'app-home',
  imports: [RouterLink],
  templateUrl: './home.html',
  styleUrl: './home.css',
})
export class Home {

users=[
  {id:'1', name:'Alice',age:30,email:'alice@example.com'},
  {id:'2', name:'Bob',age:25,email:"bob@example.com"},
  {id:'3', name:'Charlie',age:35,email:"charlie@example.com"},
  {id:'4', name:'David',age:28,email:"david@example.com"}
]
}
```
## 🔹 Step 3: Access Parameters in Component
```ts
// user.ts
import { Component } from '@angular/core';
import { ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-user',
  imports: [],
  templateUrl: './user.html',
  styleUrl: './user.css',
})
export class User {
  name:null|string="";
  constructor(private route:ActivatedRoute) {}

  ngOnInit(){
    this.route.params.subscribe(params=>{
      console.log(params);
      this.name=params['name'];
    })
}
}
```
* user.html
```html
<h1>user {{name}}</h1>
```
# Forms in Angular
* Forms are used for Login,Sign up, Email Subscription, Adding  or updating data in DB
* **Types of Forms in Angular**
1. **Reactive** : Complex Validation
2. **Template-driven** : Simple form
# Basic Reactive Forms
* app.html file
```html
<h1>Basic of React Forms</h1>
<form action="" method="post">
    <input type="text" placeholder="enter name" [formControl]="name">
    <br><br>
    <input type="text" placeholder="enter password" [formControl]="password">
    <br><br>
    <button type="button" (click)="displayValue()">Login</button>
</form>
```
* app.ts file
```ts
import { Component, signal, effect } from '@angular/core';
import { RouterLink, RouterOutlet } from '@angular/router';
import { Header } from "./header/header";
import { Pagenotfound } from './pagenotfound/pagenotfound';
import { FormControl, ReactiveFormsModule } from '@angular/forms';

@Component({
  selector: 'app-root',
  imports: [ReactiveFormsModule],
  templateUrl: './app.html',
  styleUrl: './app.css'
})
export class App {
   
  name = new FormControl('Sithkar');
  password = new FormControl('123');

  displayValue(){
    console.log(this.name.value,this.password.value);
  }
}
```










  









