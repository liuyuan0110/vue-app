<template>
<div>
    <ul>
        <li v-for="(menuItem) in menuItemList" :key="menuItem.key" v-on:click="setView(menuItem)">
            {{ menuItem.menuName }}
        </li>
    </ul>
</div>
    
</template>
<script>
export default {
  name: "Header",
  data() {
    return {
      menuItemList: [],
      year: this.getYear()
    };
  },
  methods: {
    getMenuItemList: function () {
      debugger;
      let menuItemList = [
        { key: "001", menuName: "首页", menuView: "Index", menuViewType: "component" },
        { key: "002", menuName: "导航栏", menuView: "Navigator", menuViewType: "component" },
      ];
      this.menuItemList = menuItemList;
    },
    getYear: function () {
        debugger;
        return new Date().getFullYear();
    },
    setView: function (menuItem) {
        debugger;
        this.$parent.setFrameView(menuItem);
    }
  },
  created() {
      debugger;
      this.getMenuItemList();
  }
};
</script>
<style>
li {
    float: left;
    margin-left: 5px;
    list-style-type: none;
    height: 30px;
    width: 80px;
    line-height: 30px;
    text-align: center;
    border: 1px solid red;
    border-radius: 5px;
}
</style>
