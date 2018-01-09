# Angular

### :HOST-CONTEXT (css)
```css
:host-context(.selected) .container {
  background: red; 
  color: white;
}
```
_Anywhere above component host_ [doc](https://angular.io/guide/component-styles#host)

### :HOST (css)
```css
:host(.theme-dark) .container {
  background: #000000;
}
```
[doc](https://angular.io/guide/component-styles#host-context)

### Router EnableTracing
```TypeScript
imports: [ RouterModule.forRoot(routes, { enableTracing: true }) ],
```
[doc](https://angular.io/api/router/RouterModule#forRoot)

### Style binding
```html
<div [style.width]="someValue + '%'">Hey!</div>
<!-- equals to -->
<div [style.width.%]="someValue">Hey!</div>
```
[doc](https://angular.io/guide/template-syntax#style-binding)

### Display when ready
```html
<user-list [users]="users" *ngIf="users"></user-list>
<!-- observable -->
<user-list [users]="users$ | async as users" *ngIf="users"></user-list>
```

### Component recursion
```TypeScript
@Component({
 selector: 'children',
 template: `
 <div *ngFor="let child of children">
     <children [children]="child.children" *ngIf="child.children"></children>
 </div> `,
})
export class ChildrenComponent {
 @Input() children;
}
```

### Key events
```html
<input (keyup.enter)="doSomething(1)"
       (keyup.arrowUp)="doSomething(2)"
       (keyup.arrowDown)="doSomething(3)"
       (keyup.esc)="doSomething(4)" />
```

### Page title change
```TypeScript
public constructor(private title : Title ) {}
ngOnInit {
 this.title.setTitle('Page title');
}
```

### Template If Then Else
```html
<div *ngIf="condition; then thenBlock else elseBlock"></div>
<ng-template #thenBlock>condition === true</ng-template>
<ng-template #elseBlock>condition === false</ng-template>
```

### Global events
```html
<div (window:resize)="onResize($event)">...</div>
<div (document:click)="onClick($event)">...</div>
```

### Model driven controll `get`
```TypeScript
user.get('details').get('account').get('email')
// equals to
user.get('details.account.email')
```

### Unsubscribe all subscription
```TypeScript
 subscriptions : new Subscription();
 
 ngOnInit() {
   this.subscriptions.add(...subscribe(...));
   this.subscriptions.add(...subscribe(...));
 }
 
 ngOnDestroy() {
   this.subscriptions.unsubscribe();
 }
 ```
 
 ### Barrel
```TypeScript
/* before */
// code1.ts file
import { UsersComponent } from '../users/users.component.ts';
import { UserDetailsComponent } from '../users/user-details.component.ts';
import { UserHeaderComponent } from '../users/user-header.component.ts';
import { UsersService } from '../users/users.service.ts';

/* after */
// index.ts file:
export * from './users.component';
export * from './user-details.component';
export * from './user-header.component';
export * from './users.service';

// code1.ts file
import {
 UsersComponent,
 UserDetailsComponent,
 UserHeaderComponent,
 UsersService
} from './users'
```

### tsconfig.json imports
```javascript
"baseUrl": "src",
"paths": {
  "@env/*": ["environments/*"]
}
```

### Observable from child element event
```TypeScript
@Component({
 selector: 'cont',
 template: `<button type="button">Click</button> `,
})
export class ContComponent {
  @ViewChild('button') button;
  clicks$:Observable<any>;

  ngOnInit() {
    this.clicks$ = Observable.fromEvent(this.button.nativeElement, 'click');
  }
}
```

### Highlight link/tab/button by active route
```html
<button routerLink="tab1" routerLinkActive="class1 class2" #route="routerLinkActive">
  Tab1<span *ngIf="route.isActive"> *</span>
</button>
<button routerLink="tab2" [routerLinkActive]="['class1', 'class2']">Tab2</button>
```
[RouterLinkActive](https://angular.io/api/router/RouterLinkActive)
