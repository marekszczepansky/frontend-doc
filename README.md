# Frontend

## Angular

### :HOST-CONTEXT
```css
:host-context(.selected) .container {
  background: red; 
  color: white;
}
```
_Anywhere above component host_

### :HOST
```css
:host(.theme-dark) .container {
  background: #000000;
}
```

### Router EnableTracing
```typescript
imports: [ RouterModule.forRoot(routes, { enableTracing: true }) ],
```

### Style binding
```html
<div [style.width]="someValue + '%'">Hey!</div>
<!-- equals to -->
<div [style.width.%]="someValue">Hey!</div>
```

### Display when ready
```html
<user-list [users]="users" *ngIf="users"></user-list>
<!-- observable -->
<user-list [users]="users$ | async as users" *ngIf="users"></user-list>
```

### Component recurence
```typescript
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
