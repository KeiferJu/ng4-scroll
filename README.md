# ng4-scroll

##瀑布流加载


###使用

import { ScrollEventModule } from 'ngx-scroll-event';

@NgModule({
  imports: [
    ...,
    ScrollEventModule,
    ...,
  ]
})
export class AppModule { }
```

In your template you may now add the `detect-scroll` attribute and `(onScroll)` event to any element.
you can also add `[bottomOffset]` to change when reaching bottom is alert is true, defaults to 100, the value should be a number in pixels.

```typescript
// app.awesome.component.ts

...
import { ScrollEvent } from 'ngx-scroll-event';
...

@Component({
   ...
   template: `...
        <div detect-scroll (onScroll)="handleScroll($event)" [bottomOffset]="200">
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
        <div>
   ...`,
})
export class AwesomeComponent {
  public handleScroll(event: ScrollEvent) {
    console.log('scroll occurred', event.originalEvent);
    if (event.isReachingBottom) {
      console.log(`the user is reaching the bottom`);
    }
    if (event.isWindowEvent) {
      console.log(`This event is fired on Window not on an element.`);
    }

  }
}
```
