<template lang="pug">
.index.container.mt-5
    .index__container.d-flex.flex-between.brd-1.p-4
        .index__left.lists.w-40.brd-1.p-4
            list-source(v-for='(item, index) in listsAmount' :key="item.id" :index="index" @changeArray="updateCurrentArray" )
        .index__right.w-40.brd-1.p-4
            .list-result.brd-1.mt-2
                .list-name List 1
                .list-content
                    list-result(v-for="item in itemArray01"  :key="item.id" :fluidblock="item")
            .list-result.brd-1.mt-2
                .list-name List 2
                .list-content
                    list-result(v-for="item in itemArray02"  :key="item.id" :fluidblock="item")
            .list-result.brd-1.mt-2
                .list-name List 3
                .list-content
                    list-result(v-for="item in itemArray03"  :key="item.id" :fluidblock="item")
            .list-result.brd-1.mt-2
                .list-name List 4
                .list-content
                    list-result(v-for="item in itemArray04"  :key="item.id" :fluidblock="item")
            .list-result.brd-1.mt-2
                .list-name List 5
                .list-content
                    list-result(v-for="item in itemArray05"  :key="item.id" :fluidblock="item")
</template>

<script>
import ListSource from "../components/ListSource";
import ListResult from "../components/ListResult";
export default {
  name: "Index",
  components: { ListResult, ListSource },
  props: {},
  data: () => ({
    listsAmount: 5,
    itemsAmount: 4,
    itemArray01: [],
    itemArray02: [],
    itemArray03: [],
    itemArray04: [],
    itemArray05: [],
    selectedItems: [],
  }),
  created() {},
  mounted() {},
  methods: {
    updateCurrentArray(args) {
      switch (args[1]) {
        case 1:
          this.itemArray01 = args[0];
          break;
        case 2:
          this.itemArray02 = args[0];
          break;
        case 3:
          this.itemArray03 = args[0];
          break;
        case 4:
          this.itemArray04 = args[0];
          break;
        case 5:
          this.itemArray05 = args[0];
          break;
      }
    },
  },
};
</script>

<style scoped lang="scss"></style>
