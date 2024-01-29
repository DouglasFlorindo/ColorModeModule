# Color Mode JavaScript Module Documentation

## Overview

The Color Mode Module is a complete JavaScript module made to update and toggle between light and dark color modes on a web page. It has the option to use local storage for persisting user preferences and supports automatic mode detection based on the user's browser settings.

## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
3. [API Reference](#api-reference)
4. [Contributing](#contributing)
5. [License](#license)

## Installation

To use the Color Mode Module in your project, you can include the JavaScript file in your HTML:

```html
<script src="path/to/colorModeModule.js"></script>
```

## Usage

### Setting your CSS file

To guarantee that the correct style is being used, make sure that your custom color mode styles are inside the ```[data-theme='light']``` or ```[data-theme='dark']``` selectors in your CSS file:

```css
/* Safety style in case data-theme attribute is not set: */
:root {
    --textColor: "black";
    --backgroundColor: "white"; 
}

/* Light color mode style: */
[data-theme="light"] :root {
    --textColor: "black";
    --backgroundColor: "white"; 
}

/* Dark color mode style: */
[data-theme="light"] :root {
    --textColor: "white";
    --backgroundColor: "black"; 
}
```

### Setting your JavaScript file

#### Importing the module

To import the functions and variables used in the module insert the following code at the top of your script:

```js
import { updateColorMode, colorMode, localStorageAvailable } from 'colorModeMoule';
```

#### Updating the color mode via localStorage

If your web page is storing the user's preference, you can update the style as soon as the DOM content is loaded by calling the ```updateColorMode()``` function with the arguments ```useLocalStorage: true``` and ```colorModePreference: null```:

```js
document.addEventListener("DOMContentLoaded", () => updateColorMode(true, null))
```

> The code won't have effect if the user manually disabled localStorage.

#### Setting the color mode

To change the color mode to a new value, call the ```updateColorMode()``` with the ```colorModePreference``` argument passing one of the following values:

- "light": set the color mode to light.
- "dark": set the color mode to dark.
- "auto": set the color mode acording to the user's browser settings.

The ```useLocalStorage``` argument will determine if the color mode value will be stored in localStorage:

```js
updateColorMode(true|false, "light"|"dark"|"auto");
```

### API Reference

#### Function

```js
updateColorMode(useLocalStorage, colorModePreference)
```

Updates or sets the color mode.

- ```useLocalStorage``` (boolean): Indicates whether to use local storage for persisting preferences.
- ```colorModePreference``` (string): Specifies the desired color mode:
    - ```"light"```: set the color mode to light.
    - ```"dark"```: set the color mode to dark.
    - ```"auto"```: set the color mode acording to the user's browser settings.
    - ```null```: the color mode will be retrieved from localStorage.

#### Variables

- ```colorMode```: Holds the current color mode ("auto", "light", "dark").
- ```localStorageAvailable```: Indicates whether local storage is available.

### Contributing

Feel free to contribute to the project by opening issues or submitting pull requests.

### License

This project is licensed under the MIT License.