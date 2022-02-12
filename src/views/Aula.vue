<template>
<div>
  <div v-if="loading">
    <PageLoading/>
  </div>
  <transition>
    <div v-if="api">
      <h2>{{api.nome}}</h2>
      <div class="video">
         <iframe width="1280" height="720" src="https://www.youtube.com/embed/fYR9L2ZmodM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
      </div>
    </div>
  </transition>
</div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "aula",
  props: ["aula"],
  mixins: [fetchData],
  created() {
    this.fetchData(`/aula/${this.aula}`);
  },
  beforeRouteUpdate(to, from, next) {
    this.fetchData(`/aula/${to.params.aula}`);
    next();
  }

}
</script>

<style>
.video {
  position: relative;
  padding-bottom: 56.25%;
}

.video iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

</style>