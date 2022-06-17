<template>
  <div class="hero">
    <!-- Dekstop -->
    <div class="d-none d-md-block">
      <div class="row mt-4">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Populer Event</strong><br />
                in Your Page
              </h2>
              <p>Temukan event populer untuk anda</p>
              <router-link class="btn btn-success" to="/event">
                <b-icon-arrow-right></b-icon-arrow-right> Temukan
              </router-link>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <img src="../assets/img/hero.png" width="100%" alt="" />
        </div>
      </div>
    </div>

    <!-- Mobile -->
    <div class="d-sm-block d-md-none">
      <div class="row mt-4">
        <div class="col-md-6">
          <img src="../assets/img/hero.png" width="100%" alt="" />
        </div>
        <div class="col-md-6 mb-4">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Populer Event</strong><br />
                in Your Page
              </h2>
              <p>Temukan event populer untuk anda</p>
              <button class="btn btn-success">
                <b-icon-arrow-right></b-icon-arrow-right> Temukan
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: `HeroComp`,
};
</script>

<style>
</style>