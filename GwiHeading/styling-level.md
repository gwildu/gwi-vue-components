```html
<GwiHeading styling-level="1">markup-level 1</GwiHeading>
<GwiHeading :styling-level="2">markup-level 2 with number prop</GwiHeading>
<GwiHeading styling-level="3">markup-level 3</GwiHeading>
<GwiHeading styling-level="4">markup-level 4</GwiHeading>
<GwiHeading styling-level="5">markup-level 5</GwiHeading>
<GwiHeading styling-level="6">markup-level 6</GwiHeading>
```

results in:
```html
<h3 class="gwi-text__heading gwi-text__heading--1">styling-level 1</h3>
<h3 class="gwi-text__heading gwi-text__heading--2">styling-level 2 with number</h3>
<h3 class="gwi-text__heading gwi-text__heading--3">styling-level 3</h3>
<h3 class="gwi-text__heading gwi-text__heading--4">styling-level 4</h3>
<h3 class="gwi-text__heading gwi-text__heading--5">styling-level 5</h3>
<h3 class="gwi-text__heading gwi-text__heading--6">styling-level 6</h3>
```
