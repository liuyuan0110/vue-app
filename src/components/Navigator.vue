<template>
<div>
    <div>
        当前歌曲：{{currentSong.data.song.name}}
    </div>
    <table>
        <tr>
                <td></td>
                <td>歌曲名</td>
                <td>作者</td>
                <td>操作</td>
            </tr>
        <tr v-for="(song, index) in songList" :key="song.albumid">
            <td>{{index + 1}}</td>
            <td :title="song.data.albumname">{{ song.data.albumname }}</td>
            <td>{{(song.data.singer || [])[0].name}}</td>
            <td >
                <button v-on:click="playSong(song.data.songmid)">播放</button>
                <button v-if="song.data.songmid == currentSong.data.song.mid" v-on:click="pauseSong()">停止</button>
            </td>
        </tr>
    </table>
</div>
  
</template>

<script>
const player = new QMplayer();
export default {
  name: "Navigator",
  data() {
    return {
        songList: [],
        currentSong: {
          data : {
              song : {
                  name : "",
                  mid : ""
              }
          }
      }
    };
  },
  methods: {
    init: function () {
      debugger;
      //player.play("002uhVYq0xG6g5");
    },
    playSong: function (albummid) {
        debugger;
        player.play(albummid);
        this.currentSong = player;
        console.log(this.currentSong);
    },
    getSongList: function () {
      debugger;
      this.$axios
        .get("/v8/fcg-bin/fcg_v8_toplist_cp.fcg?g_tk=5381&uin=0&format=json&inCharset=utf-8&outCharset=utf-8¬ice=0&platform=h5&needNewCode=1&tpl=3&page=detail&type=top&topid=27&_=1519963122923")
        .then((response) => {
          if (response.data) {
            this.songList = response.data.songlist;
            console.log(response.data);
          }
        })
        .catch((err) => {
          alert("请求失败");
        });
    },
    pauseSong: function () {
        debugger;
        player.pause();
    }
  },
  created: function () {
    this.init();
    this.getSongList();
  },
};
</script>

<style>
</style>
