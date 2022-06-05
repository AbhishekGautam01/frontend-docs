1. **What is Angular Framework?**
* **typescript based open source front-end platform**
* **FEatures**: declarative templates, dependency injection, end to end tooling
* Service controller based approach, component based UI approach, developed considering mobile platform 

2. **TypeScript**
* Superset of JS by microsoft adds optional types, classes, async/await and compiled to plain JS
> npm install -g typescript

3. **Angular Architecture**
![architecture](./img/architecture.png)

4. **Key Components**
* Angular has below key components 
    1. **Components** : basic building block and control HTML views
    2. **Modules**: It is set of Basic building blocks like components, directives, services, etc. Application is divided into logical pieces which is called **module**
    3. **templates**: Represents the view of angular applications
    4. **Services**: Components which can be shared across entire appln
    5. **metadata**: can be used to add more data to angular class

5. **Directives**
* Adds behaviors to existing DOM
* You can build directive using below code 
```
import { Directive, ElementRef, Input } from '@angular/core';

@Directive({ selector: '[myHighlight]' })
export class HighlightDirective {
    constructor(el: ElementRef) {
       el.nativeElement.style.backgroundColor = 'yellow';
    }
}

<p myHighlight>Highlight me!</p>
```

6. **Components**
* most basic UI element, form a tree of angular components. 
* components are subset of directives. but a component always have a template
* Registered using @Component meta-data annotation, act like a UI widget, Directive add behavior to existing DOM
```
import { Component } from '@angular/core';

@Component ({
   selector: 'my-app',
   template: ` <div>
      <h1>{{title}}</h1>
      <div>Learn Angular6 with examples</div>
   </div> `,
})

export class AppComponent {
   title: string = 'Welcome to Angular world';
}
```

7. **Template**
* HTML where you can display data by binding controls to properties of an angular component. 
* A template can be stored: 
    1. **Using template property**
    ```
    import { Component } from '@angular/core';

    @Component ({
    selector: 'my-app',
    template: '
        <div>
            <h1>{{title}}</h1>
            <div>Learn Angular</div>
        </div>
    '
    })

    export class AppComponent {
    title: string = 'Hello World';
    }
    ```
    2. **Separate template file** and link it to the component using @Component metadata **templateUrl** property
    ```
    import { Component } from '@angular/core';

    @Component ({
    selector: 'my-app',
    templateUrl: 'app/app.component.html'
    })

    export class AppComponent {
    title: string = 'Hello World';
    }
    ```

8. **Modules**: modules are logical boundaries in your applications and aplication is divided into separate modules to separate the functionality of your application. 
* **app.modules.ts** root module declared with **@NgModule** decorator as below: 
```
import { NgModule }      from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent }  from './app.component';

@NgModule ({
   imports:      [ BrowserModule ],
   declarations: [ AppComponent ],
   bootstrap:    [ AppComponent ],
   providers: []
})
export class AppModule { }
```
1. **imports**: used to import other dependent modules. **browser Module** is required by default for any web-based angular app
2. **declarations**: Used to define components in the respective modules
3. **bootstrap**: Angular which components to bootstrap in the application. 
4. **provider**: used to configure set of **injectable objects** that are available **in injector of this module**
5. **entryComponents**: it is set of components dynamically loaded into the view. 

8. **Life Cycle Hooks**: **constructor -> ngOnChanges -> ngOnInit -> ngDoCheck -> ngAfterContentInit -> ngAfterContentChecked -> ngAfterViewInit -> ngAfterViewChecked -> ngOnDestroy**
    1. **ngOnChanges**: value of ***data bound property changes** then this is called
    2. **ngOnInit**: initialization of directives/components
    3. **ngDoCheck**: For detection and to act on changes that angular won't or can't detect on its own. 
    4. **ngAfterContentInit**: called in response after angular projects external content into the component's view.
    7. **ngOnDestroy**: Clean up phase just before angular destroys the directive/component

9. **data binding**: Define *8communication** between component and DOM. 
    * **4 Forms of Data Binding**: 
        1. **From the component to DOM** 
            * **Interpolation**: **{{value}}** adds the value of property
            ```
            <li>Name: {{ user.name }}</li>
            <li>Address: {{ user.address }}</li>
            ```
            * **property binding**: **\[property\] = value**: the value is passed fro component to HTML attribute
            ```
            <input name="email" [value]="user.email">
            ```
        2. **From the DOM to Component**: **Event Binding: (event)="function"** when a specified DOM event happens, it calls the specific method in the component 
        ```
        <button (click)="logout()"></button>
        ```
        3. **Two Way Data Binding**: **\[(ngModel)\]="value"**: allows data to flow both ways
        ```
        <input type="email" [(ngModel)]="user.email">
        ```
10. **metadata**: used to **decorate class** so that if can configure the expected behavior of class. 
    1. **Class Decorators**: **@Component, @NgModule**, Imported from @angular/core
    ```
    import { NgModule, Component } from '@angular/core';

    @Component({
    selector: 'my-component',
    template: '<div>Class decorator</div>',
    })
    export class MyComponent {
    constructor() {
        console.log('Hey I am a component!');
    }
    }

    @NgModule({
    imports: [],
    declarations: [],
    })
    export class MyModule {
    constructor() {
        console.log('Hey I am a module!');
    }
    }
    ```
    2. **property decorators**: **@input, @output**
    ```
    import { Component, Input } from '@angular/core';

    @Component({
        selector: 'my-component',
        template: '<div>Property decorator</div>'
    })

    export class MyComponent {
        @Input()
        title: string;
    }
    ```
    3. **method decorators**: Used for methods inside classes, eg. **@HostListener**
    ```
    import { Component, HostListener } from '@angular/core';

    @Component({
        selector: 'my-component',
        template: '<div>Method decorator</div>'
    })
    export class MyComponent {
        @HostListener('click', ['$event'])
        onHostClick(event: Event) {
            // clicked, `event` available
        }
    }
    ```
    4. **parameter decorator**: Used for parameters inside class constructors: **@inject**(optional)
    ```
    import { Component, Inject } from '@angular/core';
    import { MyService } from './my-service';

    @Component({
        selector: 'my-component',
        template: '<div>Parameter decorator</div>'
    })
    export class MyComponent {
        constructor(@Inject(MyService) myService) {
            console.log(myService); // MyService
        }
    }
    ```

11. **Angular CLI**: CLI interface to scaffold and build apps using nodejs style (commonJS) modules. 
    > npm install @angular/cli@latest
    * **Creating new project**: ng new 
    * **generating components, directives & services**
    ```
        ng generate class my-new-class: add a class to your application
        ng generate component my-new-component: add a component to your application
        ng generate directive my-new-directive: add a directive to your application
        ng generate enum my-new-enum: add an enum to your application
        ng generate module my-new-module: add a module to your application
        ng generate pipe my-new-pipe: add a pipe to your application
        ng generate service my-new-service: add a service to your application
    ```
    * **running project**: ng serve

12. **Constructor vs ngOnInit**: Ctor is used or initialization purpose, ngOnInit is used to define angular bindings. 
13. **Service**: Common functionality needs to be provided to various modules. Allows **separation of concerns for your apps** 
    * A service should be marked @Injectable , **provideIn** tells which module it can injected to 
    ```
    import { Injectable } from '@angular/core';
    import { Http } from '@angular/http';

    @Injectable({ // The Injectable decorator is required for dependency injection to work
    // providedIn option registers the service with a specific NgModule
    providedIn: 'root',  // This declares the service with the root app (AppModule)
    })
    export class RepoService{
    constructor(private http: Http){
    }

    fetchAll(){
        return this.http.get('https://api.github.com/repositories');
    }
    }
    ```
14. ***DI**: A class asks for dependencies from external sources rather than creating them itself. Angular ships with built-in dependency injection 
15. **Async Pipe**: Returns observable or promise and returns the value it has emitted. When a new value ie emitted, the pipe marks the component to be checked for changes. 
```
@Component({
  selector: 'async-observable-pipe',
  template: `<div><code>observable|async</code>:
       Time: {{ time | async }}</div>`
})
export class AsyncObservablePipeComponent {
  time = new Observable(observer =>
    setInterval(() => observer.next(new Date().toString()), 2000)
  );
}
```
20. **ngFor** directive: used in template to display each item in the list. 
```
<li *ngFor="let user of users">
  {{ user }}
</li>
```
21. **ngIf**: It is used to display components using specific conditions 
```
<p *ngIf="user.age > 18">You are not eligible for student pass!</p>
```
22. What happens when you use script tag inside template? 
* angular recognizes the value as unsafe and automatically sanitizes it, which removes the `script` tag but keeps the safe content such as text content of script tag. This eliminates risk of **script injection attach. 
````
export class InnerHtmlBindingComponent {
  // For example, a user/attacker-controlled value from a URL.
  htmlSnippet = 'Template <script>alert("0wned")</script> <b>Syntax</b>';
}
````
23. **Interpolation**: special syntax that angular converts into property binding. it is convenient alternative to property binding. representing in double curly braces {{}}, Text between property is name is component property. 
```
<h3>
  {{title}}
  <img src="{{url}}" style="height:30px">
</h3>
```
25. What are template expressions?
A template expression produces a value similar to any Javascript expression. Angular executes the expression and assigns it to a property of a binding target; the target might be an HTML element, a component, or a directive. In the property binding, a template expression appears in quotes to the right of the = symbol as in \[property\]="expression". In interpolation syntax, the template expression is surrounded by double curly braces. For example, in the below interpolation, the template expression is {{username}},

> <h3>{{username}}, welcome to Angular</h3>

27. Categorize data binding types: 

| Data Direction | Syntax | Type | 
| :---: | :---: | :---: |
| From the source to view (one way) | 1. {{expression}}, 2. \[target]="expression 3. bind-target="Expression" | Interpolation, property, attribute, class, style | 
| From view to source(one way) | 1. (target)="statement" 2. on-target="statement" | Event | 
| View to source to view (two way) | 1. [(target)]="expression" 2. bindon-target="expression" | two way | 

28. **pipes**: takes in data as input and transforms it to a desired output. eg: date pipe: 
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-birthday',
  template: `<p>Birthday is {{ birthday | date }}</p>`
})
export class BirthdayComponent {
  birthday = new Date(1987, 6, 18); // June 18, 1987
}
```


29. **parameterized pipe**: A pipe can accept any number of optional parameters to fine-tune its output. The parameterized pipe can be created by declaring the pipe name with a colon ( : ) and then the parameter value.
```
import { Component } from '@angular/core';

    @Component({
      selector: 'app-birthday',
      template: `<p>Birthday is {{ birthday | date:'dd/MM/yyyy'}}</p>` // 18/06/1987
    })
    export class BirthdayComponent {
      birthday = new Date(1987, 6, 18);
    }
```

30. **Chaining Pipes**: 
```
import { Component } from '@angular/core';

@Component({
    selector: 'app-birthday',
    template: `<p>Birthday is {{  birthday | date:'fullDate' | uppercase}} </p>` // THURSDAY, JUNE 18, 1987
})
export class BirthdayComponent {
    birthday = new Date(1987, 6, 18);
}

```

31. **Custom Pipe**: 
    1. A pipe class is decorated with pipe metadata **@Pipe** decorator, whch you can import from core angular library. 
    > @Pipe({name: 'myCustomPipe})
    2. The pipe class implements the PipeTransform interface transform method that accepts an input value followed by optional parameters and returns the transformed value.
    ```
    interface PipeTransform {
        transform(value: any, ...args: any[]): any
    }
    ```
    3. **Example of Custom Pipe**: 

    ```javscript
    import {Pipe, PipeTransform} from '@angular/core';

    @Pipe({name: 'customFileSizePipe'})
    export class FileSizePipe implements PipeTransform{
        transform(size: number, extension: string = 'MB'): string {
            return (size / (1024* 1024)).toFixed(2) + extension;
        }
    }
    ```

33. **pure vs Impure pipe**
    * PURE PIPE: Angular detects a change in value or the parameter passes to a pipe. 
    * IMPURE PIPE: it is called after every change detection cycle. like it called on every mouse click or hover over 

34. **Bootstrapping module**: Every app has atleast one module , the root module that you bootstrap to launch the app. It is commonly known as **AppModule** the default structure of app module is generated by AngularCLI as follows: 
 
```javascript
    /* JavaScript imports */
    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';
    import { FormsModule } from '@angular/forms';
    import { HttpClientModule } from '@angular/common/http';

    import { AppComponent } from './app.component';

    /* the AppModule class with the @NgModule decorator */
    @NgModule({
    declarations: [
        AppComponent
    ],
    imports: [
        BrowserModule,
        FormsModule,
        HttpClientModule
    ],
    providers: [],
    bootstrap: [AppComponent]
    })
    export class AppModule { }
    ```
```

35. **Observables**:  which support for passing message between publishers and subscribers in your app. they are mainly used for event handling, aysnc programming, and handling multiple values. It is not executed unitll a consumer subscribes to it. the subscribed consumer then receives notification untill the function completes or they unsubscribe. 

36. HttpClients: It is based on **XMLHttpRequest**. this is available from `@angular/common/http` . It provides typed request and response objects and intercept request response, supports observable APIs and suppport streamlined erroor handling. 

37. **Example of Http Client**: 
    1. Import HttpClient in root module
    ```
    import { HttpClientModule } from '@angular/common/http';
    @NgModule({
    imports: [
        BrowserModule,
        // import HttpClientModule after BrowserModule.
        HttpClientModule,
    ],
    ......
    })
    export class AppModule {}
    ```
    2. Service: 
    ```
    import { Injectable } from '@angular/core';
    import { HttpClient } from '@angular/common/http';

    const userProfileUrl: string = 'assets/data/profile.json';

    @Injectable()
    export class UserProfileService {
    constructor(private http: HttpClient) { }

    getUserProfile() {
        return this.http.get(this.userProfileUrl);
    }
    }
    ```
    3. Component subscription
    ```
    fetchUserProfile() {
    this.userProfileService.getUserProfile()
        .subscribe((data: User) => this.user = {
            id: data['userId'],
            name: data['firstName'],
            city:  data['city']
        });
    }
    ```

39. **Error Handling**: If request fails on server HttpClient return an error object instead of success response. We need to pass an callback to handle this 
```javascript
fetchUser() {
  this.userService.getProfile()
    .subscribe(
      (data: User) => this.userProfile = { ...data }, // success path
      error => this.error = error // error path
    );
}
```

40. **RxJS**: It is library for aysnc and callback based code in a functional and reactive style using **observables**. 
```javascript 
import { Observable, throwError } from 'rxjs';
import { catchError, retry } from 'rxjs/operators';
```

41. **Subscribing**: An Observable instance begins publishing values only when someone subscribes to it. So you need to subscribe by calling the subscribe() method of the instance, passing an observer object to receive the notifications.

42. **Observable**: Unique object similar to a promise that can help manage aysnc code. observables are not part of the JS lang we import it from RxJS. 
```javascript 
import { Observable } from 'rxjs';

const observable = new Observable(observer => {
  setTimeout(() => {
    observer.next('Hello from a Observable!');
  }, 2000);
});
```

43. **Observer**: an interface for a customer of push-based notifications delivered by an observable. It has below interface
```javascript
interface Observer<T> {
  closed?: boolean;
  next: (value: T) => void;
  error: (err: any) => void;
  complete: () => void;
}
```
44. **promise vs observable**: 

| Observable | Promise | 
| :---: | :---: |
| Declarative: Computation doesnt start until subscriptuon so that they can be run whenever you need the result. | Execution start immediately on creation | 
| Provide multiple values over time | Provide only one | 
| Subscribe method is used for error handling which makes centralized and predicate error handling | Push errors to child promises | 
| Provides chaining and subscription to handle complex applications | Uses only *.then()* clause 

45. **multicasting**:practice of broadcasting to a list of multiple subscribers in a single execution.
```javascript 
var source = Rx.Observable.from([1, 2, 3]);
var subject = new Rx.Subject();
var multicasted = source.multicast(subject);

// These are, under the hood, `subject.subscribe({...})`:
multicasted.subscribe({
  next: (v) => console.log('observerA: ' + v)
});
multicasted.subscribe({
  next: (v) => console.log('observerB: ' + v)
});

// This is, under the hood, `s
```

46. **Error Handling in observable**: Using a **error callback** on observer instead of relying on try catch . 
```javascript 
myObservable.subscribe({
    next(num){console.log('next num:' + num)}, 
    error(err){console.log(error)}
});
```
47. **getting completion on subscribe method** 
```javascript
myObservable.subscribe(
  x => console.log('Observer got a next value: ' + x),
  err => console.error('Observer got an error: ' + err),
  () => console.log('Observer got a complete notification')
);
```
63. **Angular Router**: it is a mechanism of navigation happens from one view to the next as user perform application tasks. 
64. **base href tag**: routing application should add element to index.html as the first child in the tag in order to indicate how to compose navigation URLs. if app folder is the application root you can set the href value as below: 
> <base href="/">
65. **Router Imports**: import {RouterModule, Routes} from '@angular/router';
66. **Router outlets**: directive from the router library and it acts as a placeholder that marks the spot in the template where the router should display the components for that outlet. . These are used like **components**
67. **router links**: The RouterLink is a directive on the anchor tags give the router control over those elements. Since the navigation paths are fixed, you can assign string values to router-link directive as below,
```html
<h1>Angular Router</h1>
<nav>
  <a routerLink="/todosList" >List of todos</a>
  <a routerLink="/completed" >Completed todos</a>
</nav>
<router-outlet></router-outlet>
```
68. **Active router links**: RouterLinkActive is a directive that toggles css classes for active routerLink bindings based on the current RouterState i.e.e that router will add CSS classes when this link is active and remove when the link is inactive. 
```html 
<h1>Angular Router</h1>
<nav>
  <a routerLink="/todosList" routerLinkActive="active">List of todos</a>
  <a routerLink="/completed" routerLinkActive="active">Completed todos</a>
</nav>
<router-outlet></router-outlet>
```

## Further here https://github.com/sudheerj/angular-interview-questions#what-is-angular-framework 