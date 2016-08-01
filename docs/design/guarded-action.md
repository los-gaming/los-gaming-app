# Guarded Action
## Abstract
We want a general way to guard actions so that they may only activate should all attached guards allow it. We want this action to play nicely with Angular Material 2 and effectively replace the `(click)="action()"` binding where appropriate.
## Usage
### Markup
```html
<button md-button (guardedAction)="act($event)">Submit</button>
```
### Typescript
```typescript
@Component({})
class SomeComponent : Component
{
    @Guard([
        () => this.auth.isAuthenticated() ? null : "You must log in to use act",
        () => this.auth.isAdmin() ? null : "You must be an admin to use act"
    ])
    act($event) {
        console.log("I'm logged in, and I'm an admin!");
    }
}
```

## Challenges
- Integrate with existing Angular Material 2 actionable components such as md-button, md-menu-item, and others.
- Port this behavior to Angular 1