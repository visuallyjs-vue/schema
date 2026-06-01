<script setup>
import { ref } from "vue";
import { isNode, isPort } from "@visuallyjs/browser-ui"
import { InspectorComponent } from "@visuallyjs/browser-ui-vue";
import { datatypes, cardinalities } from "../definitions";
import {
    PROPERTY_CARDINALITY,
    TABLE, VIEW, COLUMN, RELATIONSHIP
} from "../constants";

const currentType = ref('')

const refresh = (obj) => {
    const ct = isNode(obj) ? obj.data.type : isPort(obj) ? COLUMN : RELATIONSHIP
    currentType.value = ct
}

const renderEmptyContainer = () => currentType.value = ''
</script>

<template>
    <InspectorComponent :renderEmptyContainer="renderEmptyContainer" :refresh="refresh">
        <template v-if="currentType === TABLE">
            <div>Table Name</div>
            <input type="text" vjs-att="name" vjs-focus="true"/>
        </template>

        <template v-else-if="currentType === VIEW">
            <div>View Name</div>
            <input type="text" vjs-att="name" vjs-focus="true"/>
            <div>Query</div>
            <textarea vjs-att="query" rows="10"/>
        </template>

        <template v-else-if="currentType === COLUMN">
            <div>Name</div>
            <input type="text" vjs-att="name" vjs-focus="true"/>
            <div>Datatype</div>
            <label v-for="d in datatypes" :key="d.id">
                <input type="radio" vjs-att="datatype" name="datatype" :value="d.id"/>{{d.description}}
            </label>
        </template>

        <template v-else-if="currentType === RELATIONSHIP">
            <div>Cardinality</div>
            <label v-for="c in cardinalities" :key="c.id">
                <input type="radio" :name="PROPERTY_CARDINALITY" :vjs-att="PROPERTY_CARDINALITY" :value="c.id"/>{{c.name}}
            </label>
        </template>
    </InspectorComponent>
</template>
