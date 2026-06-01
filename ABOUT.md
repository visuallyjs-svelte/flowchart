### Summary
This demo features a flowchart editor built with the specialized `DiagramComponent`. It provides a high-level API for creating diagrams with standard shapes and orthogonal connectors.

### Components Used
- `DiagramProvider`: Specialized provider for diagramming context.
- `DiagramComponent`: A high-level component specifically for node-and-edge diagrams.
- `DiagramPaletteComponent`: A ready-to-use palette for diagram shapes.
- `ControlsComponent`: Standard canvas controls.
- `ExportControlsComponent`: Controls for exporting the diagram.
- `MiniviewComponent`: Overview map.
- `InspectorComponent`: (In `InspectorComponent.svelte`) Uses `ColorPickerComponent` and `EdgeTypePickerComponent` for editing.

### Component Options
#### `DiagramComponent`
- `url`: The data source for the diagram.
- `options`: A comprehensive configuration object including:
    - `shapes`: Defines the available shape sets (e.g., `FLOWCHART_SHAPES`, `BASIC_SHAPES`).
    - `edges`: Configures edge behavior (connectors, labels, avoidance).
    - `cells`: Configures cell behavior like rotation.
    - `grid`: Configures the background grid.
    - `lasso`: Enables lasso selection.

#### `DiagramPaletteComponent`
- `selectAfterAdd`: Boolean to automatically select a shape after it's dropped onto the canvas.

### Stylesheet Requirement
The `visuallyjs.css` stylesheet is required.

```css
@import "@visuallyjs/browser-ui/css/visuallyjs.css";
```
