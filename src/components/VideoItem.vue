<template>
  <div>
    <a class="mb-7 group">
      <VideoItemThumbnall :index="index" />
      <VideoItemInfo :index="index" />
    </a>
  </div>
</template>

<script>
import VideoItemThumbnall from "./VideoItemThumbnall.vue";
import VideoItemInfo from "./VideoItemInfo.vue";

export default {
  components: {
    VideoItemThumbnall,
    VideoItemInfo,
  },

  props: ["index"],
};
</script>
