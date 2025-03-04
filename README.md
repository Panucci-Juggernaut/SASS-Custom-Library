# Panucci - A Lightweight CSS Library

Panucci is a lightweight CSS library designed for upcoming developers. It provides a set of customizable and extendable styles and components to help you build beautiful web applications quickly and efficiently. This library is similar to what Bootstrap uses, making it easy to get started if you are familiar with Bootstrap.

## Table of Contents

- [Getting Started](#getting-started)
- [Usage](#usage)
- [Customization](#customization)
- [Extending the Library](#extending-the-library)
- [Development](#development)
- [License](#license)

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed on your machine:

- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/)

### Installation

1. Clone the repository:

```sh
git clone https://github.com/your-username/sass-custom-library.git
cd sass-custom-library
```

2. Install the dependencies:

```sh
npm install gulp gulp-sass sass --save-dev
```

3. Build the CSS files:

```sh
npx gulp
```

## Usage

To use Panucci in your project, include the generated CSS file in your HTML:

```html
<link rel="stylesheet" href="css/index.css">
```

You can now use the provided classes in your HTML to style your elements. For example:

```html
<div class="container">
  <h2 class="text-primary">Primary Text</h2>
  <button class="btn-primary">Click Me</button>
</div>
```

## Customization

Panucci is built with SASS, making it easy to customize. You can modify the SASS variables to change the default styles.

### Changing Colors

To change the primary color, update the `$primary` variable in `_variables.scss`:

```scss
$primary: #ff5733 !default;
```

### Adding New Colors

To add a new color, update the `$colors` map in `_variables.scss`:

```scss
$colors: (
  "primary": $primary,
  "secondary": $secondary,
  "error": $error,
  "info": $info,
  "new-color": #123456,
);
```

## Extending the Library

You can extend Panucci by adding new components or utilities.

### Adding a New Component

1. Create a new SASS file in the `components` directory, e.g., `_new-component.scss`
2. Define your styles in the new file
3. Import the new component in `index.scss`:

```scss
@use 'components/new-component';
```

### Adding a New Utility

1. Create a new SASS file in the root directory, e.g., `_new-utility.scss`
2. Define your utility classes in the new file
3. Import the new utility in `index.scss`:

```scss
@use 'new-utility';
```

## Development

### Project Setup

1. Initialize a new project:

```sh
npm init -y
```

2. Install development dependencies:

```sh
npm install gulp gulp-sass sass --save-dev
```

3. Create a gulpfile.js:

```javascript
const { src, dest, watch, series } = require('gulp');
const sass = require('gulp-sass')(require('sass'));

function buildStyles() {
  return src('panucci/**/*.scss')
    .pipe(sass())
    .pipe(dest('css'));
}

function watchTask() {
  watch(['panucci/**/*.scss'], buildStyles);
}

exports.default = series(buildStyles, watchTask);
```

### Building the CSS

To build the CSS files, run:

```sh
npx gulp
```

This will:
1. Watch for changes in your SCSS files
2. Compile SCSS to CSS
3. Output the compiled CSS to the css directory