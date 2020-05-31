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
import { mapState } from "vuex";

export default {
  head() {
    return {
      title: "Event Listing"
    };
  },
  components: { EventCard },
  async fetch({ store, error }) {
    try {
      await store.dispatch("events/fetchEvents");
    } catch (e) {
      error({
        statusCode: 404,
        message: `Failed to fetch events data`
      });
    }
  },
  computed: { ...mapState({ events: state => state.events.events }) }
};
</script>
