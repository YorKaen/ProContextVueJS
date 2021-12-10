<template lang="pug">
.list
    .list-head.flex-start.d-flex
        button.btn.list-hide.mr-1
            span.arrow(@click="showList = !showList" :class="{hidden: !showList}")
                span
                span
        input(type="checkbox" :indeterminate="indet" v-model="checked" @click="toggleAllCheck").list-mode.mr-1
        .list-name List {{ index+1 }}
    .list-content.pl-6(v-show="showList")
        .item(v-for='item in listItemsArray' :key="item.id").d-flex.flex-between.mb-1
            .item-left.d-flex
                input(type="checkbox" v-model="item.isChecked" @click="checkboxToggle(item)" @change="addCategoryChild").mr-1
                .item-name Item {{ item.index }}
            .item-right.d-flex
                input(type="number" min="0" v-model="item.amount" @change="addCategoryChild").input-number.mr-2
                input(type="color" v-model="item.color" @change="addCategoryChild").input-color
</template>

<script>
export default {
  name: "ListSource",
  components: {},
  props: ["index"],
  data: () => ({
    listItemsArray: [
      {
        index: 1,
        isChecked: false,
        amount: 4,
        color: "#fe1b1b",
      },
      {
        index: 2,
        isChecked: false,
        amount: 24,
        color: "#ed9612",
      },
      {
        index: 3,
        isChecked: false,
        amount: 14,
        color: "#4ccb12",
      },
      {
        index: 4,
        isChecked: false,
        amount: 12,
        color: "#12abed",
      },
    ],
    showList: false,
    activated: false,
    checked: false,
    indet: false,
    checkedRows: [],
  }),
  created() {},
  mounted() {
    this.addCategoryChild();
  },
  methods: {
    addCategoryChild() {
      this.$emit("changeArray", [this.listItemsArray, this.index + 1]);
    },
    indetCheck(val) {
      switch (val) {
        case 0:
          this.indet = false;
          this.checked = false;
          break;
        case 1:
          this.indet = true;
          this.checked = false;
          break;
        case 2:
          this.indet = true;
          this.checked = false;
          break;
        case 3:
          this.indet = true;
          this.checked = true;
          break;
        case 4:
          this.indet = false;
          this.checked = true;
          break;
      }
    },
    checkboxToggle(val) {
      if (this.checkedRows.indexOf(val.index) === -1) {
        this.checkedRows.push(val.index);
      } else {
        this.checkedRows.splice(this.checkedRows.indexOf(val.index), 1);
      }
      this.indetCheck(this.checkedRows.length);
    },
    toggleAllCheck() {
      if (!this.checked) {
        this.showList = true;
        for (let i = 0; i < this.listItemsArray.length; i++) {
          this.listItemsArray[i].isChecked = true;
        }
        this.checkedRows.push(1, 2, 3, 4);
      } else {
        for (let i = 0; i < this.listItemsArray.length; i++) {
          this.listItemsArray[i].isChecked = false;
        }
        this.checkedRows = [];
      }
      this.indetCheck(this.checkedRows.length);
    },
  },
};
</script>

<style lang="scss" scoped>
.input-number {
  max-width: 6ch;
  border: none;
}
.input-color {
  max-width: 2em;
  border: none;
}
.list {
  &-head {
    align-items: center;
  }
  .btn {
    display: flex;
    align-items: center;
  }
}
.arrow {
  width: 1.25rem;
  height: 1.25rem;
  display: inline-block;
  position: relative;
  line-height: 22px;
  transition: all 0.2s ease;
  span {
    top: 0.5rem;
    position: absolute;
    width: 0.75rem;
    height: 0.1rem;
    background-color: black;
    display: inline-block;

    &:first-of-type {
      left: 0;
      transform: rotate(45deg);
    }
    &:last-of-type {
      right: 0;
      transform: rotate(-45deg);
    }
  }
  &.hidden {
    transform: rotate(-90deg);
    span {
      &:first-of-type {
      }

      &:last-of-type {
      }
    }
  }
}
</style>
