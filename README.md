# Teamapp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 13.1.2.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.


***

## Angular Concepts Covered

### 1. Angular Setup

#### Node Installation
Install latest node from official web site.
To check the node installation use below commands
```
node -v
npm -v
```
#### Angular CLI
Install Angular CLI using following command
```
npm install -g @angular/cli
```
To check the installation of Angular CLI
```
ng version
```
To create project
```
ng new Teamapp
```
To run the application locally 
```
npm start
```
or
```
ng serve
```

### 2. HTML File
To begin with editing view! start with 
>app.component.html

Remove boilerplate code and start editing the above file to play with the view.

### 3. Styles
To work with styles we have two ways!

Editing Component level css

>app.component.css

We can also achieve this by editing global css file
>styles.css

To add any third party css like semantic-ui-css, bootstrap, etc.

```
npm install semantic-ui-css
```

After installing the required css module we need to include it in the project, for this we can add below import statement in global css file i.e **styles.css**.

```
@import "semantic-ui-css/semantic.css";
```
### 4. STATE
We add state of the component in app.component.ts
```
export class AppComponent {
  newMemberName = '';
  errorMessage = '';
  members: string[] = [];
  numberOfTeams: number | "" = "";
  teams: string[][] = [];
}
```
### 5. Event Handlers
To handle events like onclick, oninput, onchange, etc.


Inside app.component.html

```
<!-- event: input -->

    <input 
        #addMemberInput 
        type="text"
        placeholder="Name"
        [value]="newMemberName"
        (input)="onInput(addMemberInput.value)" />

<!-- event: click -->

    <button (click)="addMember()">Add</button>

```

Inside app.component.ts

```
  addMember() {
    // logic goes here.
  }

  onInput(member: string) {
    // logic goes here.
  }
```

### 6. STRUCTURAL and Attribute DIRECTIVES

**Structural directives** are used for shaping or reshaping HTML DOM by adding, removing elements.

Example for structural directives are *ngIf and *ngFor

```
<div class="teams-container" *ngIf="teams.length">
    <app-team *ngFor="let team of teams; let i = index" [team]="team" [index]="i"></app-team>
</div>
```

**Attribute directives** are used to change the appearance or behavior of DOM element.

Example for attribute directives is use of **[]**. In below example to make value of **value** equals to that of the state, we wrap the **value** as **[value]**

```
<input type="text" placeholder="Name" [value]="newMemberName" />
```

Note:
> We can apply many attribute directives to one host element, But can apply only one structural directive to a host element.

### 7. Components

To add a new component to the project, run below command. This will add new component to the project and also includes it module **declarations**.
```
ng g component team
```

To include the component, we have to use ```selector: 'app-team'```
```
<app-team></app-team>
```
To pass data from parent component to the child component, in our case from **app** component to **team** component:

Inside team.component.ts (*#child component*)

```
import { Input } from '@angular/core';

@Input() team: string[] = [];
@Input() index = 0;
```

Inside app.component.html (*#parent component*)

```
<app-team [index]="i"></app-team>
```

### 8. PIPES
[PIPES](https://angular.io/api?type=pipe)

Angular Pipes transform the output. You can think of them as makeup rooms where they beautify the data into a more desirable format. They do not alter the data but change how they appear to the user.

    # Pipes are defined using the pipe “|” symbol.
    # Pipes can be chained with other pipes.
    # Pipes can be provided with arguments by using the colon (:) sign.