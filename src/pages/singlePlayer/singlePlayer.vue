<template>
  <div class="single-player">
    <div class="wrapper">
      <word-typer :class="{loading}" :loading="loading"></word-typer>
    </div>
    <race></race>
    <div class="wrapper">
      <transition name="fade">
        <stats v-show="finished"></stats>
      </transition>
      <transition name="fade">
        <button class="btn-save" v-show="finished" @click="showSaveScore = true">Save</button>
      </transition>
    </div>
    <!-- NOTE: width = wrapper width / 2 -->
    <!-- This is to line up the graph's svg stroke with other components -->
    <!-- Hack? Maybe. Aesthetic? Yes. -->
    <transition name="fade">
      <speed-graph v-show="!loading":width="718" :height="449"></speed-graph>
    </transition>
    <save-score v-if="showSaveScore" @close="showSaveScore = false"></save-score>
  </div>
</template>

<script lang="ts" src="./singlePlayer.ts"></script>
<style lang="scss" src="./singlePlayer.scss" scoped></style>
