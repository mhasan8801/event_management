<template>
  <div class="disimpan">
    <NavbarComp :updateDisimpan="disimpans"/>

    <div class="container">
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
                disimpan
              </li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row">
        <div class="col">
          <h2><strong>Event Saya</strong></h2>
          <div class="table-responsive mt-3">
            <table class="table">
              <thead>
                <tr>
                  <th scope="col"></th>
                  <th scope="col">Foto</th>
                  <th scope="col">Nama</th>
                  <th scope="col">Prioritas</th>
                  <th scope="col">Hari</th>
                  <th scope="col">Keterangan</th>
                  <th scope="col">Hapus</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(disimpan, index) in disimpans" :key="disimpan.id">
                  <th>{{ index + 1 }}</th>
                  <td>
                    <img
                      :src="'../assets/img/' + disimpan.event.gambar" width="150"
                      class="img-fluid shadow"
                      alt=""
                    />
                  </td>
                  <td><strong>{{ disimpan.event.nama }}</strong></td>
                  <td>{{disimpan.prioritas}}</td>
                  <td>{{disimpan.event.hari}}</td>
                  <td>{{disimpan.keterangan ? disimpan.keterangan : "-" }}</td>
                  <td align="center" class="text-danger"><b-icon-trash @click="hapusDisimpan(disimpan.id)"></b-icon-trash></td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavbarComp from "@/components/NavbarComp.vue";
import axios from "axios";

export default {
  name: `disimpanView`,
  components: {
    NavbarComp,
  },
  data() {
    return {
      disimpans: [],
    };
  },
  methods: {
    setDisimpan(data) {
      this.disimpans = data;
    },
    hapusDisimpan(id) {
      axios
      .delete("http://localhost:3000/disimpan/"+id)
      .then((response) => {
        console.log("Hapus Berhasil : ", response);

      // Update setelah delete
      axios
      .get("http://localhost:3000/disimpan")
      .then((response) => this.setDisimpan(response.data))
      .catch((error) => console.log(error));

      })
      .catch((error) => console.log(error));
    }
  },
  mounted() {
    axios
      .get("http://localhost:3000/disimpan")
      .then((response) => this.setDisimpan(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>