<template>
  <div class="index-container">
    <div class="nav">
      <ul>
        <li>
          <router-link to="/discovery">
            <span class="iconfont icon-find-music" />
            发现音乐
          </router-link>
        </li>
        <li>
          <router-link to="/playlists">
            <span class="iconfont icon-music-list" />
            推荐歌单
          </router-link>
        </li>
        <li>
          <router-link to="/songs">
            <span class="iconfont icon-music" />
            最新音乐
          </router-link>
        </li>
        <li>
          <router-link to="/mvs">
            <span class="iconfont icon-mv" />
            最新MV
          </router-link>
        </li>
      </ul>
    </div>
    <div class="main">
      <router-view />
    </div>
    <div class="player">
      <audio ref="audioRef" :src="getUrl" controls autoplay loop />
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  name: 'Content',
  computed: {
    ...mapGetters({ getUrl: 'url/getUrl' })
  }
}
</script>
