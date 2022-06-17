<template>
  <div class="foot-detail">
    <NavbarComp />
    <div class="container">
      <!-- breadcrumb -->
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/event" class="text-dark">Event</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">
                Event Order
              </li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col md-6">
          <img
            :src="'../assets/img/' + event.gambar"
            class="img-fluid shadow"
            alt=""
          />
        </div>
        <div class="col md-6">
          <h2>
            <strong>{{ event.nama }}</strong>
          </h2>
          <hr />
          <h4>
            Pelaksanaan : <strong>Hari {{ event.hari }}</strong>
          </h4>
          <form class="mt-4" v-on:submit.prevent>
            <div class="form-group">
              <label for="jumlah_pemesanan"> Jumlah Pesan </label>
              <input
                type="number"
                class="form-control"
                v-model="pesan.jumlah_pemesanan"
              />
            </div>
            <div class="form-group">
              <label for="keterangan"> Keterangan </label>
              <textarea
                v-model="pesan.keterangan"
                class="form-control"
                placeholder="Keterangan seperti : pedas, tambah nasi dll"
              ></textarea>
            </div>
            <button type="submit" class="btn btn-success" @click="pemesanan">
              <b-icon-cart></b-icon-cart>Pesan
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavbarComp from "@/components/NavbarComp.vue";
import axios from "axios";

export default {
  name: `EventdetailView`,
  components: {
    NavbarComp,
  },
  data() {
    return {
      event: {},
      pesan: {},
    };
  },
  methods: {
    setEvent(data) {
      this.event = data;
    },
    pemesanan() {
        this.pesan.event = this.event;
        axios
        .post("http://localhost:3000/keranjangs", this.pesan)
        .then(() => {
            this.$router.push({ path: "/keranjang"})
            console.log("Berhasil");
        })
        .catch((err) => console.log(err))
    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/events/" + this.$route.params.id)
      .then((response) => this.setEvent(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>