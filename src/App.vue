<script setup>
import {
    SurfaceProvider,
    SurfaceComponent,
    ControlsComponent,
    MiniviewComponent
} from "@visuallyjs/browser-ui-vue"

import renderOptions from './render-options'
import viewOptions from './view-options'
import modelOptions from './model-options'

import SchemaInspector from "./components/InspectorComponent.vue"
import SchemaPalette from "./components/Palette.vue"
import { ref } from "vue"

const props = defineProps({
    url: String
})

const surfaceComponent = ref(null)
</script>

<template>

        <SurfaceProvider>
            <div class="vjs-schema-builder-canvas">
                <SurfaceComponent :renderOptions="renderOptions" :modelOptions="modelOptions" :viewOptions="viewOptions" ref="surfaceComponent" url="/schema-1.json">
                    <ControlsComponent/>
                </SurfaceComponent>
            </div>
            <div class="vjs-schema-builder-rhs">
                <MiniviewComponent/>
                <SchemaPalette/>
                <SchemaInspector/>
            </div>
        </SurfaceProvider>
</template>

