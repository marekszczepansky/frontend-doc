# Frontend

## Angular

### :HOST-CONTEXT
```css
:host-context(.selected) .container {
  background: red; color: white;
}
```

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
