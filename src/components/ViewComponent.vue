<script setup>
const props = defineProps({
  obj: Object,
  model:Object
})

const {obj, model} = props

function deleteView() {
    model.removeNode(obj)
}

function editView() {
    model.setSelection(obj)
}
</script>

<template>
    <div class="vjs-schema-view vjs-schema-element">
            <div class="vjs-schema-element-name">
                <div class="vjs-schema-view-delete vjs-schema-delete vjs-schema-delete-vertex" title="Delete view" @click="deleteView"/>
                <span>{{obj.data.name}}</span>
                <div class="vjs-schema-buttons">
                    <div class="vjs-schema-edit-name vjs-schema-edit" title="Edit view" @click="editView"/>
                </div>
            </div>
            <div class="vjs-schema-view-details">{{obj.data.query}}</div>
    </div>
</template>
