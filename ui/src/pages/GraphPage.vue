<script setup lang="ts">
import { GraphMaker, GraphMakerSettings } from "@milaboratories/graph-maker";
import '@milaboratories/graph-maker/styles';
import { useApp } from "../app";

const app = useApp();

// @TODO move to defaultUi when implemented in the model
if (app.ui.graphState === undefined) {
    app.model.ui.graphState = {
        title: "Gene usage",
        chartType: "heatmap",
        template: "heatmap",
        // defaultOptions: [
        //     {
        //         inputName: "y",
        //         selectedSource: {
        //             kind: "PColumn",
        //             valueType: "Float",
        //             name: "pl7.app/vdj/diversity",
        //             axesSpec: [
        //                 {
        //                     type: "String",
        //                     name: "pl7.app/sampleId"
        //                 },
        //                 {
        //                     type: "String",
        //                     name: "pl7.app/vdj/diversityMeasure"
        //                 }
        //             ]
        //         }
        //     }
        // ]
    } satisfies GraphMakerSettings
};
</script>

<template>
    <GraphMaker :p-frame="app.model.outputs.pf" v-model="app.model.ui.graphState" />
</template>