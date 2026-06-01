<script setup>
import { uuid } from "@visuallyjs/browser-ui"
import { datatypes } from "../definitions";

const props = defineProps({
  obj: Object,
  model:Object
})

const {obj, model} = props

function addColumn() {
    model.addNewPort(obj, "column", {
        id: uuid(),
        name: "new column",
        primaryKey: false,
        datatype: datatypes[0].id
    });
}

function deleteTable() {
    model.removeNode(obj)
}

function editTable() {
    model.setSelection(obj)
}

function deleteColumn(columnId) {
    model.removePort(obj, columnId)
}

function editColumn(columnId) {
    model.setSelection(obj.getPort(columnId))
}
</script>

<template>
    <div class="vjs-schema-table vjs-schema-element">
        <div class="vjs-schema-element-name">
            <div class="vjs-schema-delete vjs-schema-delete-vertex" title="Click to delete" @click="deleteTable"/>
            <span>{{obj.data.name}}</span>
            <div class="vjs-schema-buttons">
                <div class="vjs-schema-edit-name vjs-schema-edit" title="Click to edit table name" @click="editTable"/>
                <div class="vjs-schema-new-column vjs-schema-add" title="Click to add a new column" @click="addColumn"/>
            </div>
        </div>
        <div class="vjs-schema-table-columns">
            <div v-for="c in obj.data.columns" :key="c.id" class="vjs-schema-table-column" :data-type="c.datatype" :data-primary-key="(c.primaryKey || false).toString()" :data-vjs-port="c.id" :data-vjs-scope="c.datatype" :data-vjs-source="true" :data-vjs-target="true">
                <div class="vjs-schema-table-column-delete vjs-schema-delete" @click="deleteColumn(c.id)"/>
                <div><span>{{c.name}}</span></div>
                <div class="vjs-schema-table-column-edit vjs-schema-edit" @click="editColumn(c.id)"/>
            </div>
        </div>
    </div>
</template>
