<template>
  <div class="home">
    <NavbarComp />
    <div class="container">
      <HeroComp />

      <div class="row mt-4">
        <div class="col">
          <h2>Best <strong>Events</strong></h2>
        </div>
        <div class="col">
          <router-link to="/event" class="btn btn-success float-right"
            ><b-icon-eye></b-icon-eye> Semua</router-link
          >
        </div>
      </div>

      <div class="row mb-4">
        <div class="col-md-4 mt-4" v-for="event in events" :key="event.id">
          <CardeventComp :event="event"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import NavbarComp from "@/components/NavbarComp.vue";
import HeroComp from "@/components/HeroComp.vue";
import CardeventComp from "@/components/CardeventComp.vue";
import axios from "axios";

export default {
  name: "HomeView",
  components: {
    NavbarComp,
    HeroComp,
    CardeventComp,
  },
  data() {
    return {
      events: [],
    };
  },
  methods: {
    setEvent(data) {
      this.events = data;
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/best-events")
      .then((response) => this.setEvent(response.data))
      .catch((error) => console.log(error))
  },
};
</script>
