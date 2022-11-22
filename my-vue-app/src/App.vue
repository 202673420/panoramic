<template>
    <FiveProvider :work="work">
        <FiveCanvas :width="width" :height="height" />
        <!-- 模态控制按钮组件 -->
        <ModeController />
        <!-- 自动环视组件 -->
        <LookAroundController />
        <!-- 记录和回放组件 -->
<!--        <RecorderController />-->
        <!-- 记录鼠标点击点位的组件 -->
        <MarkController style="margin-top:50px !important" />
        <!--打标签组件-->
        <TaggingController />

    </FiveProvider>
</template>

<script setup>

import { FiveProvider, FiveCanvas } from "@realsee/five/vue";
import { parseWork } from "@realsee/five";
import { ref } from "vue";
import { useWindowDimensions } from "./useWindowDimensions";

import ModeController from "./ModeController.vue";
import LookAroundController from "./LookAroundController.vue"
import RecorderController from "./RecorderController.vue";
import MarkController from "./MarkController.vue";
import TaggingController from "./TaggingController.vue";

const work = ref();
const workURL = "https://vrlab-public.ljcdn.com/release/static/image/release/five/work-sample/07bdc58f413bc5494f05c7cbb5cbdce4/work.json";

fetch(workURL).then(response => response.text()).then(text => work.value = parseWork(text));
const { width, height } = useWindowDimensions();
</script>
