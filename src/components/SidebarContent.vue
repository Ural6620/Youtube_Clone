<template>
  <SidebarSection>
    <ul>
      <SidebarNavItem icon="home" label="Home" is-active />
      <SidebarNavItem icon="fire" label="Trending" />
      <SidebarNavItem icon="collection" label="Subscriptions" />
    </ul>
  </SidebarSection>

  <SidebarSection>
    <ul>
      <SidebarNavItem icon="dublicate" label="Library" />
      <SidebarNavItem icon="clock" label="History" />
    </ul>
  </SidebarSection>

  <SidebarSection class="px-8 py-4 font-medium leading-5 border-b">
    <span class="text-sm">
      Sign in to like videos, comment, and subscribe.
    </span>
    <ButtonLogin
      class="focus:outline-none flex items-center px-2 py-0.5 mt-3 text-sm text-blue-700 uppercase border border-blue-700 rounded-sm"
    />
  </SidebarSection>
  <SidebarSection>
    <ul>
      <SidebarTitleItem label="Best of YouTube" />
      <SidebarNavItem icon="music" label="Music" />
      <SidebarNavItem icon="bullharn" label="Sports" />
      <SidebarNavItem icon="game" label="Gaming" />
      <SidebarNavItem icon="video" label="Movies" />
      <SidebarNavItem icon="news" label="News" />
      <SidebarNavItem icon="wifi" label="Live" />
      <SidebarNavItem icon="eye" label="360&deg; Video" />
    </ul>
  </SidebarSection>

  <SidebarSection>
    <ul>
      <SidebarNavItem icon="plus" label="Browse channels" />
    </ul>
  </SidebarSection>

  <SidebarSection>
    <ul>
      <SidebarTitleItem label="More from YouTube" />
      <SidebarNavItem icon="play" label="YouTube Premium" />
      <SidebarNavItem icon="wifi" label="Live" />
    </ul>
  </SidebarSection>

  <SidebarSection>
    <ul>
      <SidebarNavItem icon="gear" label="Settings" />
      <SidebarNavItem icon="flag" label="Report history" />
      <SidebarNavItem icon="question" label="Help" />
      <SidebarNavItem icon="message" label="Send feedback" />
    </ul>
  </SidebarSection>

  <SidebarSection class="px-6 py-4 text-xs font-semibold space-y-4">
    <TheFooter />
  </SidebarSection>
</template>

<script>
import ButtonLogin from "./ButtonLogin.vue";
import SidebarNavItem from "./SidebarNavItem.vue";
import SidebarTitleItem from "./SidebarTitleItem.vue";
import SidebarSection from "./SidebarSection.vue";
import TheFooter from "./TheFooter.vue";

export default {
  components: {
    ButtonLogin,
    SidebarNavItem,
    SidebarTitleItem,
    SidebarSection,
    TheFooter,
  },
};
</script>
