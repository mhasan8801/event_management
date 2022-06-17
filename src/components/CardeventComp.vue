<template>
  <div class="card shadow card-event">
    <img
      :src="'assets/img/' + event.gambar"
      class="card-img-top"
      alt="..."
    />
    <div class="card-body">
      <h5 class="card-title">{{ event.nama }}</h5>
      <p class="card-text">Pelaksanaan : Hari {{ event.hari }}</p>
      <router-link class="btn btn-success" :to="'/event/' + event.id"
        ><b-icon-cart></b-icon-cart> Pesan</router-link
      >
    </div>
  </div>
</template>

<script>
export default {
  name: `CardeventComp`,
  props: ["event"],
};
</script>

<style>
</style>