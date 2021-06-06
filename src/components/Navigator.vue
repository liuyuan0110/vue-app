<template>
  <div>navigator</div>
</template>

<script>
export default {
  name: "Navigator",
  methods: {
    init: function () {
      debugger;
      var player = new QMplayer();
      //player.play("004D8S6y2DgqLW");
    },
    getSongList: function () {
      debugger;
      axios({
        //格式a
        method: "get",
        url: "https://c.y.qq.com/v8/fcg-bin/fcg_v8_toplist_cp.fcg?g_tk=5381&uin=0&format=json&inCharset=utf-8&outCharset=utf-8¬ice=0&platform=h5&needNewCode=1&tpl=3&page=detail&type=top&topid=27&_=1519963122923",
      })
        .then(function (resp) {
          console.log(resp.data);
        })
        .catch((resp) => {
          console.log("请求失败：" + resp.status + "," + resp.statusText);
        });
    },
  },
  created: function () {
    this.init();
    this.getSongList();
  },
};
</script>

<style>
</style>
