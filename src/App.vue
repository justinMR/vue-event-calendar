<template>
  <div id="app">
    <div class="container">
      <img alt="Vue logo" src="./assets/logo.png" />
      <h1>Event Calendar</h1>
      <select v-model="selectedType">
        <option selected value="All Types">All Types</option>
        <option
          v-bind:key="event.id"
          v-bind:value="event.eventType"
          v-for="event in events"
        >{{event.eventType}}</option>
      </select>
      <div class="form-control">
        <input type="text" class="input" placeholder="Search" v-model="search" />
      </div>
      <EventList v-bind="{events: filteredEventsBySearchAndType}"></EventList>
    </div>
  </div>
</template>

<script>
import EventList from "./components/EventList.vue";
export default {
  name: "App",
  components: {
    EventList,
  },
  data: function () {
    return {
      events: [
        {
          id: 1,
          eventType: "webinar",
          date: "08/18/2020",
          time: "1:00PM",
          eventDetails:
            "How to Deliver Bottom-Line Value and Strengthen Agency Partnerships in Times of Social Unrest/Crisis",
          eventLocation: "Webinar",
        },
        {
          id: 2,
          eventType: "training",
          date: "08/18/2020",
          time: "5:00PM",
          eventDetails: "From Insights to Great Messaging - Virtual",
          eventLocation: "Virtual Workshop (Eastern Time)",
        },
        {
          id: 3,
          eventType: "1-Day",
          date: "08/19/2020",
          time: "3:00 PM",
          eventDetails:
            "Leveraging Data & Insights to Drive Digital Engagement and Growth, Presented by Deloitte Digital",
          eventLocation: "Virtual Event (Eastern Time)",
        },
        {
          id: 4,
          eventType: "Committee",
          date: "09/23/2020",
          time: "7:00 PM",
          eventDetails: "Reskilling the organization",
          eventLocation: "Via Teams",
        },
        {
          id: 5,
          eventType: "Conference",
          date: "09/25/2020",
          time: "10:00 AM",
          eventDetails: "2020 ANA Media & MEasurement Conference",
          eventLocation: "Virtual Event (Eastern Time)",
        },
        {
          id: 6,
          eventType: "webinar",
          date: "09/25/2020",
          time: "10:00 AM",
          eventDetails: "2020 ANA Media & MEasurement Conference",
          eventLocation: "Virtual Event (Eastern Time)",
        },
      ],
      search: "",
      selectedType: "",
    };
  },
  computed: {
    filteredEventsBySearchAndType: function () {
      return this.events
        .filter((event) => {
          return event.eventDetails
            .trim("")
            .toLowerCase()
            .match(this.search.trim("").toLowerCase());
        })
        .filter((event) => {
          if (this.selectedType === "" || this.selectedType === "All Types") {
            return event;
          } else if (this.selectedType === event.eventType) {
            return event;
          }
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
