<template>
  <div>
    <div
      v-for="home in homes"
      :key="home.objectID"
      style="float: left; margin: 10px"
    >
      <nuxt-link :to="{ name: 'home-id', params: { id: home.objectID } }">
        <HomeCard :home="home" />
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "index",
  head: () => ({
    title: "Homepage",
    meta: [
      {
        name: "description",
        value: "This is a homepage!",
        hid: "description",
      },
    ],
  }),

  async asyncData({ $dataApi }) {
    return {
      homes: (await $dataApi.getHomes()).json.hits
    }
  }
};
</script>
