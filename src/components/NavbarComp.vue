<template>
    <nav class="navbar navbar-expand-lg">
      <div class="container">
        <a class="navbar-brand" href="#">Event Management</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link class="nav-link" to="/">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/event">Events</router-link>
            </li>
          </ul>
          <ul class="navbar-nav ml-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link class="nav-link" to="/disimpan"><b-icon-save></b-icon-save>
              Disimpan
              
              <span class="badge badge-success ml-2">{{ updateDisimpan ? updateDisimpan.length : jumlah_pesanan.length }}</span>
              </router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
</template>

<script>
import axios from "axios";

export default {
  name: `NavbarComp`,
  data() {
    return {
      jumlah_pesanan: []
    }
  },
  props: ['updateDisimpan'],
  methods: {
    setJumlah(data) {
      this.jumlah_pesanan = data
    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/disimpan")
      .then((response) => this.setJumlah(response.data))
      .catch((error) => console.log(error))
  }
};
</script>

<style>
</style>