# ngx-categorized-select

[![npm](https://img.shields.io/npm/v/ngx-categorized-select.svg?style=flat-square)](https://www.npmjs.com/package/ngx-categorized-select)
[![npm](https://img.shields.io/npm/dm/ngx-categorized-select.svg?style=flat-square)](https://www.npmjs.com/package/ngx-categorized-select)
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](https://github.com/georgebyte/ngx-categorized-select/blob/master/LICENSE)

A component for Angular 2+ to select categorized items.

![ngx-categorized-select gif](images/ngx-categorized-select.gif?raw=true "ngx-categorized-select")

## How to use?

First install `ngx-categorized-select` package from npm:

```bash
npm install --save ngx-categorized-select
```

Then import `CategorizedSelectComponent` from `ngx-categorized-select` and add it to a module's `declarations` list:

```typescript
import { CategorizedSelectComponent } from 'ngx-categorized-select';

@NgModule({
  declarations: [
    ...
    CategorizedSelectComponent,
  ],
  ...
})
export class ExampleModule { }
```

`categorized-select` component can now be used in templates like this:

```html
<categorized-select [categorizedItems]="categorizedItems"
                    [config]="config"
                    (onApply)="callback($event)">
</categorized-select>
```

### Attributes:
| Attribute        | Type                          |
|:---------------- |:----------------------------- |
| categorizedItems | Category[]                    |
| config           | Config?                       |
| onApply          | EventEmitter<SelectionItem[]> |

### Example:

**app.module.ts:**

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { CategorizedSelectComponent } from 'ngx-categorized-select';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent,
    CategorizedSelectComponent,
  ],
  imports: [
    BrowserModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

**app.component.ts:**

```typescript
import { Component } from '@angular/core';
import { Config, Category, SelectionItem } from 'ngx-categorized-select';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  config: Config = {
    enableKeyBindings: true,
  };

  categorizedItems: Category[] = [
    {
      name: 'First category',
      key: 'first_category',
      items: [
        {
          name: 'First item in first category',
          value: 'first_item',
          description: 'Item 1',
          selected: false,
        },
        {
          name: 'Second item in first category',
          value: 'second_item',
          description: 'Item 2',
          selected: false,
        },
        {
          name: 'Third item in first category',
          value: 'third_item',
          description: 'Item 3',
          selected: false,
        },
      ],
    },
    {
      name: 'Second category',
      key: 'second_category',
      items: [
        {
          name: 'First item in second category',
          value: 'first_item',
          description: 'Item 1',
          selected: false,
        },
        {
          name: 'Second item in second category',
          value: 'second_item',
          description: 'Item 2',
          selected: false,
        },
        {
          name: 'Third item in second category',
          value: 'third_item',
          description: 'Item 3',
          selected: false,
        },
      ],
    }
  ];

  applySelection (selection: SelectionItem[]): void {
    console.log(selection);
  }
}
```

**app.component.html:**

```html
<div class="categorized-select-container" style="width: 300px; height: 400px; border: 1px solid #f5f5f5;">
  <categorized-select [categorizedItems]="categorizedItems"
                      [config]="config"
                      (onApply)="applySelection($event)">
  </categorized-select>
</div>
```
