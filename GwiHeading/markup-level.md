## Code

```html
<GwiHeading markup-level="1">markup-level 1</GwiHeading>
<GwiHeading :markup-level="2">markup-level 2 with number prop</GwiHeading>
<GwiHeading markup-level="3">markup-level 3</GwiHeading>
<GwiHeading markup-level="4">markup-level 4</GwiHeading>
<GwiHeading markup-level="5">markup-level 5</GwiHeading>
<GwiHeading markup-level="6">markup-level 6</GwiHeading>
```

results in:
```html
<h1 class="gwi-text__heading gwi-text__heading--3">markup-level 1</h1>
<h2 class="gwi-text__heading gwi-text__heading--3">markup-level 2 with number</h2>
<h3 class="gwi-text__heading gwi-text__heading--3">markup-level 3</h3>
<h4 class="gwi-text__heading gwi-text__heading--3">markup-level 4</h4>
<h5 class="gwi-text__heading gwi-text__heading--3">markup-level 5</h5>
<h6 class="gwi-text__heading gwi-text__heading--3">markup-level 6</h6>
```
