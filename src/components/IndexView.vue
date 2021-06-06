<template>
  <div>
    <keep-alive>
      <component v-bind:is="currentView"></component>
    </keep-alive>
  </div>
</template>
<script>
export default {
  name: "IndexView",
  data() {
    return {
        currentView:() => import("../components/Index.vue")
    };
  },
  methods: {
    getView: function (memuItem) {
      debugger;
      if (memuItem.menuViewType == "component") {
        this.currentView = () => import("../components/" + memuItem.menuView + ".vue") ;
      } else {
        return null;
      }
    },
  },
};
</script>
<style>
</style>
