<template>
  <div>
    <NavbarComp />
    <div class="container">
      <div class="row mt-4">
        <div class="col">
          <h2>Daftar <strong>Event</strong></h2>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col">
          <div class="input-group mb-3">
            <input
              v-model="search"
              type="text"
              class="form-control"
              placeholder="Cari Event disini"
              aria-label="Cari Event disini"
              aria-describedby="basic-addon1"
              @keyup="searchEvent"
            />
            <span class="input-group-text" id="basic-addon1">
              <b-icon-search></b-icon-search>
            </span>
          </div>
        </div>
      </div>

      <div class="row mb-4">
        <div class="col-md-4 mt-4" v-for="event in events" :key="event.id">
          <CardeventComp :event="event" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import NavbarComp from "@/components/NavbarComp.vue";
import CardeventComp from "@/components/CardeventComp.vue";
import axios from "axios";

export default {
  name: `EventsView`,
  components: {
    NavbarComp,
    CardeventComp,
  },
  data() {
    return {
      events: [],
      search: '',
    };
  },
  methods: {
    setEvent(data) {
      this.events = data;
    },
    searchEvent() {
      axios
      .get("http://localhost:3000/events?q="+this.search)
      .then((response) => this.setEvent(response.data))
      .catch((error) => console.log(error));
    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/events")
      .then((response) => this.setEvent(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>