## Clase: BrowserView

> Crear y controlar vistas.

**Note:**: La API de BrowserView es experimental y puede ser cambiada o elindad enl futuro versiones de Electron.

Proceso: [Principal](../glossary.md#main-process)

`BrowserView` puede ser usado para incrustar contenido web adicional en `BrowserWindow`. Es como una ventana hija, excepto que esta relativamente posicionada respecto a su ventana propietaria. Se puede considerar como una alternativa al tag `webview`.

## Ejemplo

```javascript
// En el proceso principal.
const {BrowserView, BrowserWindow} = require('electron')

let win = new BrowserWindow({width: 800, height: 600})
win.on('closed', () => {
  win = null
})

let view = new BrowserView({
  webPreferences: {
    nodeIntegration: false
  }
})
win.setBrowserView(view)
view.setBounds({ x: 0, y: 0, width: 300, height: 300 })
view.webContents.loadURL('https://electron.atom.io')
```

### `new BrowserView([options])` *Experimental*

* `opciones` Objecto (opcional) 
  * Objeto `webPreferences` (opcional) - vea [BrowserWindow](browser-window.md).

### Métodos Estáticos

#### `BrowserView.fromId(id)`

* `id` Entero

Devuelve `BrowserView` - La vista con el proveido `id`.

### Propiedades de Instancia

Los objetos creados con `new BrowserView` tienen las siguientes propiedades:

#### `view.webContents` *Experimental*

Un objeto [`WebContents`](web-contents.md), que pertenece a esta vista.

#### `view.id` *Experimental*

Un `Integer` representa el id único de la vista.

### Métodos de Instancia

Los objetos creados con `new BrowserView` tiene los siguientes métodos de instancia:

#### `view.setAutoResize(options)` *Experimental*

* `options` Object 
  * `width` Boolean - If `true`, la anchura de la vista se expanderá y se encogerá junto a la ventana. Por defecto `false`.
  * `height` Boolean - If `true`, la altura de la vista se expanderá y se encogerá junto a la ventana. Por defecto `false`.

#### `view.setBounds(bounds)` *Experimental*

* `bounds` [Rectangle](structures/rectangle.md)

Redimensiona y mueve la vista a los limites proporcionados en relación a la ventana.

#### `view.setBackgroundColor(color)` *Experimental*

* `color` String - Color en forma `#aarrggbb` o `#argb`. El canal alfa es opcional.