<template>
  <div class="background">
    <OrbitComponent class="orbit-item" :period="180" :radius="100" is-clockwise :start-stage="15">
      <template #item>
        <v-icon color="green-darken-2" icon="mdi-domain" size="large"></v-icon>
      </template>
    </OrbitComponent>
    <OrbitComponent class="orbit-item" :period="360" :radius="200" :start-stage="60" is-clockwise />
    <OrbitComponent class="orbit-item" :period="480" :radius="300" :start-stage="45" />
    <OrbitComponent class="orbit-item" :period="720" :radius="350" />
  </div>
</template>

<script lang="ts">
export default {
  name: "BackgroundComponent",
};
</script>

<script setup lang="ts">
import OrbitComponent from '@/components/Orbit/index.vue'

</script>

<style scoped lang="scss">
.background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  text-align: center;

  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(to top,
      #283e51,
      #0a2342);
}

.orbit-item {
  position: absolute;
}
</style>
