<template>
  <div id="tbody">
    <div id="header">
      <Header/>
    </div>
    <div id="view">
      <IndexView ref="indexView"></IndexView>
    </div>
  </div>
</template>

<script>
import Header from './components/Header'
import IndexView from './components/IndexView'

export default {
  name: 'App',
  components: {
    "Header": Header,
    "IndexView": IndexView
  },
  methods: {
    setFrameView: function (menuItem) {
      debugger;
      this.$refs.indexView.getView(menuItem);
    }
  }
}
</script>

<style>
#header {
  height: 10%;
  width: 100%;
}
#view {
  height: 90%;
  width: 100%;
}
#tbody {
  height: 100%;
  width: 100%;
}
html,body {
  height: 100%;
}
</style>
