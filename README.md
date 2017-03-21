# d3-molecule

**d3-molecule** is an open-source library for learning Chemical Bonding in an interactive way.
* Still a WIP to add subtle additions, optimizations.
* Watch/ Star it for further  updates.

Check out an example here. [Demo](https://arpitnarechania.github.io/d3-molecule/)

Screenshot:
![Screenshot](https://raw.githubusercontent.com/arpitnarechania/d3-molecule/master/assets/screenshot.png)

# Installation

Download d3-molecule using npm.

```
npm install d3-molecule --save-dev
cd d3-molecule
npm install
```

To use this library then, simply include d3.js, jquery, Molecule.js and Molecule.css:

``` html
<script src="/path/to/jquery.min.js"></script>
<script src="/path/to/d3.min.js"></script>
<script src="/path/to/dist/css/Molecule.css"></script>
<script src="/path/to/dist/js/Elements.js"></script>
<script src="/path/to/dist/js/Examples.js"></script>
<script src="/path/to/dist/js/Molecule.js"></script>
```

# Basic Usage

To use this library, you must create a container element and instantiate a new Molecule:

```html
<div id="container"></div>
```


Setting chart parameters
``` javascript

var key = "Benzene";
var basis = "Atomic Weight";

var options = {
        domElement: "#container",
        uniqueId: 1,
        width: 500,
        height: 500,
        borderThickness: 1,
        borderColor: "#000000",
        background: "#ffffff",
        charge: -1000,
        friction: 0.9,
        alpha: 0.1,
        theta: 0.8,
        linkStrength: 1,
        gravity: 0.1,
        maxAtomRadius: 6,
        colorScheme:["#2AA9CC", "#FCF78A"],
        bondThickness: 2,
        bondColor: "#000000",
        atomBorderThickness: 2,
        atomBorderColor: "#000000",
        atomTextColor: "#000000",
        atomSizeBasis: basis,
        boundingBox: true,
        borderRadiusX: 5,
        borderRadiusY: 5,
        detailedTooltips: true
    };

    var Elements = {};

    function loadPeriodicTableElements() {
        for (var i = 0; i < periodicTableData.length; i++) {
            // Preparing a Javascript Object of all Elements
            Elements[periodicTableData[i]["Symbol"]] = periodicTableData[i];
        }
    }
    loadPeriodicTableElements();

    for (var i = 0; i < Examples[key].nodes.length; i++) {
        Examples[key].nodes[i]["size"] = Elements[Examples[key].nodes[i]["atom"]][basis];
    }

    var molecule = new Molecule(Examples[key],options);
    molecule.render();
    
```

## Options

| Option                        | Description                                                               | Type     | Example
| ----------------------------- | ------------------------------------------------------------------------- | -------- | -------------------------- |
| `domElement`                  | The DOM element to append the molecule to                                 | string   | `'#container'`             |
| `uniqueId`                    | A Unique ID in case multiple molecules are added (as in the demo)         | number   | `1`                        |
| `width`                       | Width of the svg container                                                | number   | `500`                      |
| `height`                      | Height of the svg container                                               | number   | `500`                      |
| `borderThickness`             | Thickness of the border of the svg container                              | number   | `1`                        |  
| `borderColor`                 | Color of the border of the svg container                                  | string   | `'#000000'`                |
| `background`                  | Background color of the svg container                                     | string   | `'#FFFFFF'`                |
| `charge`                      | The Repulsion/ Attraction force between atoms                             | number   | `-1000`                    |
| `friction`                    | The friction parameter of a force directed graph                          | number   | `0.9`                      |
| `alpha`                       | The alpha parameter of a force directed graph                             | number   | `0.1`                      |
| `theta`                       | The theta parameter of a force directed graph                             | number   | `0.8`                      |
| `linkStrength`                | The linkStrength parameter of a force directed graph                      | number   | `1`                        |
| `gravity`                     | The gravity parameter of a force directed graph                           | number   | `0.1`                      |
| `maxAtomRadius`               | Radius of the biggest atom in the molecule                                | number   | `6`                        |
| `colorScheme`                 | Color scheme of the atoms                                                 | list     | `["#2AA9CC", "#FCF78A"]`   |
| `bondThickness`               | Bond thickness                                                            | number   | `1`                        |
| `bondColor`                   | Bond Color                                                                | string   | `'#000000'`                |
| `atomBorderThickness`         | Atom border thickness                                                     | string   | `1`                        |
| `atomBorderColor`             | Atom border color                                                         | string   | `'#000000'`                |
| `atomTextColor`               | Atom text color                                                           | string   | `'#000000'`                |
| `atomSizeBasis`               | Basis on which the atom circle svgs be rendered                           | string   | `'Atomic Radius'`          |
| `boundingBox`                 | If the molecule should be constrained inside the svg container            | boolean  | `true`                     |
| `borderRadiusX`               | SVG container's border (X) parameter                                      | number   | `5`                        |
| `borderRadiusY`               | SVG container's border (Y) parameter                                      | number   | `5`                        |
| `detailedTooltips`            | If detailed info about the element to be shown on hover or not            | boolean  | `true`                     |

# Advanced Usage and Features
* Clicking the atom selects it for deleting,fixing,etc (Check the example)
* Clicking the svg view port selects it for deleting,refreshing, recycling etc (Check the example)
* Clicking on 2 atoms, joins them by a bond
* Clicking on a bond, toggles the bond type
* Double clicking a bond, removes it
* Double clicking an atom, removes it and its bonds
* Lock/ Unlock atoms to their position if needed.
* Hide/ Show atoms if needed.
* Drag and Resizing of molecule container using the jquery-ui library.
* Option to Export molecule as a PNG image
* Some examples exist in the Examples.js file

# Test (WIP)
* Unit test cases in the testrunner.html
* Start a simple HTTP server and go to http://localhost:<post>/testrunner.html
* The test cases will run for the demo example

# Author

Arpit Narechania
arpitnarechania@gmail.com

# License

MIT