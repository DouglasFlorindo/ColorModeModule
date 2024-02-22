# Color Mode JavaScript Module Documentation

## Overview

The Color Mode Module is a complete JavaScript module made to update and toggle between light and dark color modes on a web page. It has the option to use local storage for persisting user preferences and supports automatic mode detection based on the user's browser settings.

## Table of Contents

1. [Usage](#usage)
2. [API Reference](#api-reference)
3. [Contributing](#contributing)
4. [License](#license)

## Usage

### Setting your CSS file

To guarantee that the correct style is being used, make sure that your custom color mode styles are inside the ```:root.lightMode``` or ```:root.darkMode``` selectors in your CSS file:

```css
/* Light color mode style: */
:root.lightMode {
    --textColor: "black";
    --backgroundColor: "white"; 
}

/* Dark color mode style: */
:root.darkMode {
    --textColor: "white";
    --backgroundColor: "black"; 
}

/* Safety style in case root class is not set (won't override previous styles because of specificity): */
:root {
    --textColor: "black";
    --backgroundColor: "white"; 
}
```

### Setting your JavaScript file

#### Importing the module

To import the functions and variables used in the module insert the following code at the top of your script:

```js
import { updateColorMode, colorMode, localStorageAvailable } from 'colorModeMoule';
```

#### Updating the color mode via localStorage

If your web page is storing the user's preference, you can update the style by adding the ```colorModeModule.min.js``` code into your ```<head>``` tag, and then calling the ```updateColorMode()``` function with the arguments ```useLocalStorage: true``` and ```colorModePreference: null```:

```html
<head>
    <script>
        // colorModeModule.min.js code goes here.
        updateColorMode(true, null);
    </script>
</head>
```

> The code won't have effect if the user manually disabled localStorage.

Copying the code into your ```<head>``` tag is especially important to avoid flashing an undesired style before the code updates the color mode.

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
