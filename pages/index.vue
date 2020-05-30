<template>
  <div>
    <h1>Events</h1>
    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    ></EventCard>
  </div>
</template>

<script>
import EventCard from "~/components/EventCard";

export default {
  head() {
    return {
      title: "Event Listing"
    };
  },
  components: { EventCard },
  async asyncData({ $axios }) {
    const { data } = await $axios
      .get("http://localhost:3000/events")
      .catch(res => {
        console.error({
          statusCode: 503,
          message: "Unable to fetch events from API try again later"
        });
      });

    return {
      events: data
    };
  }
};
</script>
