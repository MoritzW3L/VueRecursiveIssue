<template>
    <div id="layer-select">
        Entries: {{ data.length }}
        <recursive-control v-for="child in data" :key="child.id" :data="child"/>
    </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator"
import  RecursiveControl from "./RecursiveControl.vue"

export interface DataDTO{
    id: string;
    children: DataDTO[];
}

@Component({
    components: {
        RecursiveControl
    }
})
export default class LayerControl extends Vue{
    data: DataDTO[] = [];

    mounted(){
        this.data = this.fetchData();
    }

    private fetchData(){
        // here, the data would be loaded via Ajax-call or whatever have you
        return [
            {
                "id": "top",
                "children": [
                    {
                        "id": "lvl1-1",
                        "children": []
                    },
                    {
                        "id": "lvl1-2",
                        "children": []
                    }
                ]
            }
        ];
    }
}
</script>

<style>
</style>