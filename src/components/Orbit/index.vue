<template>
  <div class="orbit">
    <div class="container" :style="{ bottom: coordY + 'px', left: coordX + 'px' }">
      <slot name="item"></slot>
      <div v-if="!$slots.item" class="item"></div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "OrbitComponent",
};
</script>

<script setup lang="ts">
import { ref, computed } from "vue";
import { IProps } from "./types";

const props = withDefaults(defineProps<IProps>(), {
  radius: 400,
  period: 60,
  startStage: 0
});

const angle = ref(2 * Math.PI * props.startStage / 100);
const diameter = ref(2 * props.radius + 'px')

const coordX = computed(() => props.radius * Math.cos(angle.value));
const coordY = computed(() => props.radius * Math.sin(angle.value));

setInterval(() => {
  const direction = props.isClockwise ? -1 : 1;
  angle.value = angle.value + direction * 2 * Math.PI / (100 * props.period)
}, 10)

</script>

<style scoped lang="scss">
.orbit {
  border: 1px solid white;
  width: v-bind(diameter);
  aspect-ratio: 1;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  position: relative;
}

.item {
  width: 20px;
  aspect-ratio: 1;
  border-radius: 50%;
  background-color: white;
}
</style>
