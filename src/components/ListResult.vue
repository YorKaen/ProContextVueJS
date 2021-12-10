<template lang="pug">
.row.mb-1
    .block-wrapper.d-flex.p-1.flex-wrap(v-if="fluidblock.amount > 0")
        .block.mr-1.mt-1(v-for="block in fluidblock.amount" :key="block.id" :style="{ backgroundColor: fluidblock.color}"  @click="fluidblock.amount--")
    .block-wrapper(v-else).d-flex.p-1
        .txt.txt-black Тут пусто
</template>

<script>
export default {
  name: "ListResult",
  components: {},
  props: ["fluidblock"],
  data: () => ({}),
  created() {},
  mounted() {},
  methods: {},
};
</script>

<style lang="scss" scoped>
.block {
  width: 0.8em;
  height: 0.8em;
  background-color: black;
}
</style>
