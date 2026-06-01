<script lang="ts">
    import { LINE_WIDTHS } from "./constants";
    import {ColorPickerComponent, EdgeTypePickerComponent, InspectorComponent} from "@visuallyjs/browser-ui-svelte"
    import {Base} from "@visuallyjs/browser-ui";

    let currentType = $state("")

    function renderEmptyContainer() {
        currentType = ''
    }

    function refresh(obj: Base) {
        currentType = obj.objectType
    }
</script>

<InspectorComponent refresh={refresh} className="vjs-flowchart-inspector"
					renderEmptyContainer={renderEmptyContainer}>
	{#if currentType==='Node'}
		<div class="vjs-inspector-section">
			<div>Label</div>
			<input type="text" vjs-att="label" vjs-focus/>
		</div>
		<div class="vjs-inspector-section">
			<div>Fill Color</div>
			<ColorPickerComponent propertyName="fill"/>
		</div>

		<div class="vjs-inspector-section">
			<div>Text Color</div>
			<ColorPickerComponent propertyName="color"/>
		</div>

		<div class="vjs-inspector-section">
			<div>Outline Color</div>
			<ColorPickerComponent propertyName="outline"/>
		</div>

		<div class="vjs-inspector-section">
			<div>Outline width</div>
			<select vjs-att="outlineWidth" vjs-datatype="integer">
				{#each LINE_WIDTHS as lw}
					<option value={lw}>{lw}</option>
				{/each}
			</select>
		</div>
	{/if}

	{#if currentType==='Edge'}
		<div class="vjs-inspector-section">
			<div>Label</div>
			<input type="text" vjs-att="label"/>
		</div>
		<div class="vjs-inspector-section">
			<div>Line style</div>
			<EdgeTypePickerComponent propertyName="lineStyle"/>
		</div>
		<div class="vjs-inspector-section">
			<div>Markers</div>
			<EdgeTypePickerComponent propertyName="markers"/>
		</div>
		<div class="vjs-inspector-section">
			<div>Line width</div>
			<select vjs-att="lineWidth" vjs-datatype="integer">
				{#each LINE_WIDTHS as lw}
					<option value={lw}>{lw}</option>
				{/each}
			</select>
		</div>
	{/if}

</InspectorComponent>

