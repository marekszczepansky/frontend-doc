# Typescript
### Typed ES5 map
```TypeScript
export interface SimpleChanges {
    [propName: string]: SimpleChange;
}
```

### Callback with prototype function
```TypeScript
['ala','Ela','olA'].map(str=> str.toLocaleUpperCase());
///equals to
['ala','Ela','olA'].map(Function.prototype.call, String.prototype.toLocaleUpperCase);
```
