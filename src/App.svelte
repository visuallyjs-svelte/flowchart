<script lang="ts">
	import { FLOWCHART_SHAPES, BASIC_SHAPES, CONNECTOR_TYPE_ORTHOGONAL, FlowchartBasicEdgeMappings } from "@visuallyjs/browser-ui"
    import {
        ControlsComponent,
        DiagramComponent,
        DiagramPaletteComponent,
        DiagramProvider, ExportControlsComponent, MiniviewComponent
    } from "@visuallyjs/browser-ui-svelte";
    import InspectorComponent from "./InspectorComponent.svelte";

    const url="/dataset.json"

    const diagramOptions = {
        zoomToFit: true,
        shapes:[FLOWCHART_SHAPES, BASIC_SHAPES],
        edges: {
            avoidVertices: true,
            propertyMappings: FlowchartBasicEdgeMappings(),
            allowUnattached: true,
            connector: {
                type: CONNECTOR_TYPE_ORTHOGONAL,
                options: {
                    cornerRadius: 10
                }
            },
            showLabels: true
        },
        cells: {
            rotationStops: 4,
        },
        grid: {
            size: {
                width: 50,
                height: 50
            }
        },
        lasso: true,
        beforeStartConnect: () => {
            return {markers: "targetArrow"}
        }
    }

</script>

<DiagramProvider>
	<div class="vjs-flowchart-palette">
		<DiagramPaletteComponent selectAfterAdd={true}/>
	</div>
	<div class="vjs-flowchart">
		<DiagramComponent url={url} options={diagramOptions}/>
		<ControlsComponent/>
		<ExportControlsComponent/>
		<MiniviewComponent className="vjs-flowchart-miniview"/>
	</div>
	<InspectorComponent/>

</DiagramProvider>
