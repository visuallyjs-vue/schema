### About this Demo

This Vue application demonstrates a **Database Schema Builder** built with **VisuallyJS**.

### VisuallyJS Components Used

The demo utilizes several components from the `@visuallyjs/browser-ui-vue` package:

- **SurfaceProvider**: Provides the VisuallyJS context.
- **SurfaceComponent**: The main canvas for the schema builder.
- **ControlsComponent**: UI controls for the surface.
- **MiniviewComponent**: Displays a small navigation map.

### Component Options

The `SurfaceComponent` is configured with:

- **renderOptions**: Configures the rendering of the schema elements.
- **viewOptions**: Defines how tables and columns are displayed.
- **modelOptions**: Configures the data model behavior.

### CSS Requirement

For the VisuallyJS components to render correctly, the standard VisuallyJS stylesheet must be included in the project. In this demo, it is imported in `src/main.js`:

```javascript
import "@visuallyjs/browser-ui/css/visuallyjs.css"
```
