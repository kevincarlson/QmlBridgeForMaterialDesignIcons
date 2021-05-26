# QmlBridgeForMaterialDesignIcons

This project provides a look up table for using the Material Design Icons font in Qt/QML projects. The font contains thousands of icons designed to match Android's native icon set, which should help make applications that target mobile devices feel more at home on that platform.

The look up table is released under the terms of the MIT license, in order to permit usage in commercial applications distributed through the various app stores. The complete licensing terms are included at the top of the Icon.js file. This repository contains a copy of the Material Design Icons web font, which is distributed under the terms of the Apache Software License, version 2.0.

## Using The Icons in a QML Project

1. Download the Material Design Icons font, available at  [https://materialdesignicons.com/](https://materialdesignicons.com/)
2. Add the font file, and Icon.js from this project to the project's QRC file
3. When initializing the application from C++, add the font to the font database, `QFontDatabase::addApplicationFont(":/materialdesignicons-webfont.ttf");`
4. Import `Icon.js` in any QML file where icons will be referenced: `import "Icon.js" as MdiFont`
5. Add the desired icon to any QML item that can display text
    * Set font.family to "Material Design Icons"
    * Set the text property to the desired property of MdiFont.Icon, e.g. `MdiFont.Icon.mdiFileImage`
    
For a more thorough step by step guide, as well as an explanation of the design process, see [https://kevincarlson.codes/using-material-design-icons-with-qml/](https://kevincarlson.codes/using-material-design-icons-with-qml/).

## Example

A simple, reusable QML Icon Button may look like this:

```
import QtQuick 2.7

import QtQuick.Controls 2.0
import "Icon.js" as MdiFont

Button {
    implicitHeight: 48
    implicitWidth: 48
    font.pointSize: 24
    font.family: "Material Design Icons"
}
```

The control could be used as follows, for a simple formatting toolbar:

```
import QtQuick 2.7
import QtQuick.Controls 2.0
import QtQuick.Layouts 1.1
import "Icon.js" as MdiFont

ToolBar {
    height: 56
    RowLayout {
        IconButton {
            text: MdiFont.Icon.formatBold
            checkable: true
        }

        IconButton {
            text: MdiFont.Icon.formatItalic
            checkable: true
        }

        IconButton {
            text: MdiFont.Icon.formatUnderline
            checkable: true
        }
        
        Item {
            width: 8
        }

        IconButton {
            text: MdiFont.Icon.formatIndentDecrease
        }

        IconButton {
            text: MdiFont.Icon.formatIndentIncrease
        }
    }
}
```
