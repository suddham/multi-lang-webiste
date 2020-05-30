<template>
  <div>
    <h1>{{ event.title }}</h1>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: this.event.title,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "What you need to know about " + this.event.title || ""
        }
      ]
    };
  },
  async asyncData({ $axios, error, params }) {
    const { data } = await $axios
      .get("http://localhost:3000/events/" + params.id)
      .catch(res => {
        console.error({
          statusCode: 503,
          message: "Unable to fetch event #" + params.id + ""
        });
      });

    return {
      event: data
    };
  }
};
</script>
