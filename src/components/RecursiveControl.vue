<template>
    <div>
        <hr />
        <span>
            Id: {{ data.id}}<br />
            Entries: {{ data.children.length }}<br />
            Children: {{ $children.length}}
        </span>
        <div class="indent">
            <!-- this get rendered only in develop-mode -->
            <recursive-control v-for="child in data.children" :key="child.id" :data="child"/>
        </div>
    </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator"
import { DataDTO } from "./ParentControl.vue"

@Component
export default class RecursiveControl extends Vue{
    @Prop({ required: true }) readonly data!: DataDTO;
}
</script>

<style scoped>
div.indent{
    padding-left: 10px;
}
</style>