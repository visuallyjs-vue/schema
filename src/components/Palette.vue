<script setup>
import { PaletteComponent } from "@visuallyjs/browser-ui-vue";
import { PALETTE_MODE_TAP } from "@visuallyjs/browser-ui";
import { TABLE } from "../constants.js";

function dataGenerator (el) {
    const type = el.getAttribute("data-vjs-type"),
        base = {
            name:el.getAttribute("data-vjs-type"),
            type
        };

    if (type === TABLE) {
        base.columns = []
    } else {
        base.query =''
    }

    return base
}
</script>

<template>
    <PaletteComponent
            class="vjs-schema-palette"
            :mode="PALETTE_MODE_TAP"
            :selectAfterAdd="true"
            :dataGenerator="dataGenerator">

        <div class="vjs-schema-palette-item" data-vjs-type="table">Add Table</div>
        <div class="vjs-schema-palette-item" data-vjs-type="view">Add View</div>

    </PaletteComponent>
</template>
