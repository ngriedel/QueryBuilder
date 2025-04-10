# Angular Query Builder

A dynamic, configurable query builder for Angular 19+ with PrimeNG and Tailwind CSS integration.

## Overview

This project is a modernized and enhanced version of the original [angular2-query-builder](https://github.com/zebzhao/angular-query-builder) by zebzhao. It has been completely refactored to work seamlessly with Angular 19+, PrimeNG components, and Tailwind CSS.

The query builder provides an intuitive interface for creating complex queries through a drag-and-drop interface with customizable fields, operators, and conditions.

## Features

- 🚀 Built for Angular 19+ using standalone components
- 🧩 Seamless integration with PrimeNG components
- 💅 Beautiful styling with Tailwind CSS
- 🔄 Supports reactive forms with FormControl
- 🌳 Hierarchical rule sets with unlimited nesting
- 🧪 Entity/field relationship support
- 🎨 Fully customizable templates
- 📱 Responsive design for all screen sizes

## Installation

```bash
npm install @yourusername/angular-query-builder
```

## Basic Usage

Import the query builder component in your standalone component:

```typescript
import { Component } from '@angular/core';
import { FormControl, ReactiveFormsModule } from '@angular/forms';
import { QueryBuilderComponent } from '@yourusername/angular-query-builder';

@Component({
  selector: 'app-example',
  standalone: true,
  imports: [
    CommonModule,
    ReactiveFormsModule,
    QueryBuilderComponent,
    // Include directives and PrimeNG components as needed
  ],
  template: `
    <query-builder [formControl]="queryCtrl" [config]="config"></query-builder>
  `
})
export class ExampleComponent {
  queryCtrl = new FormControl({
    condition: 'and',
    rules: []
  });
  
  config = {
    fields: {
      age: { name: 'Age', type: 'number' },
      name: { name: 'Name', type: 'string' },
      // Add more fields as needed
    }
  };
}
```

## Demo Example

Our demo showcases two implementations:

1. A vanilla version using basic Angular styling
2. A PrimeNG version with rich UI components

The example demonstrates:
- Field selection with various data types (string, number, boolean, date, etc.)
- Conditional operators (AND/OR)
- Nested rule groups
- Custom input templates

## Configuration

```typescript
// Basic configuration
const config = {
  fields: {
    name: { 
      name: 'Name',  // Display name
      type: 'string' // Data type
    },
    age: { 
      name: 'Age', 
      type: 'number',
      operators: ['=', '>', '<'] // Custom operators
    },
    gender: {
      name: 'Gender',
      type: 'category',
      options: [
        { name: 'Male', value: 'm' },
        { name: 'Female', value: 'f' }
      ]
    }
  }
};

// Entity-based configuration
const entityConfig = {
  entities: {
    physical: { name: 'Physical Attributes' },
    nonphysical: { name: 'Nonphysical Attributes' }
  },
  fields: {
    age: { 
      name: 'Age', 
      type: 'number', 
      entity: 'physical' // Associate with entity
    },
    // More fields...
  }
};
```

## Customization

Use structural directives to customize each part of the query builder:

```html
<query-builder [config]="config">
  <!-- Custom field selector template -->
  <ng-container *queryField="let rule; let fields = fields; let onChange = onChange">
    <p-dropdown 
      [options]="fields" 
      [(ngModel)]="rule.field"
      (onChange)="onChange($event.value, rule)">
    </p-dropdown>
  </ng-container>
  
  <!-- Custom input for string type -->
  <ng-container *queryInput="let rule; type: 'string'; let onChange = onChange">
    <input 
      class="w-full border rounded p-2" 
      [(ngModel)]="rule.value"
      (input)="onChange()">
  </ng-container>
  
  <!-- More custom templates... -->
</query-builder>
```

## Development

To set up the development environment:

```bash
# Clone the repository
git clone https://github.com/yourusername/angular-query-builder.git
cd angular-query-builder

# Install dependencies
npm install

# Start development server
ng serve
```

## Building the Library

```bash
# Build the library
ng build query-builder

# Build the demo application
ng build query-builder-demo
```

## Special Thanks

- [zebzhao](https://github.com/zebzhao) for the original angular2-query-builder library
- [Claude AI](https://claude.ai) from Anthropic for assistance in refactoring the codebase and improving accessibility
- The Angular team for the excellent Angular 19+ framework
- PrimeNG for their comprehensive UI component library
- Tailwind CSS for the flexible styling system

## License

MIT
