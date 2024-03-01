<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <div class="my-3">
          <input type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?">
      </div>
      <div class="my-3 text-muted">menampilkan 4 dari 4</div>
      <div class="row">
        <div class="col-lg-2">
          <div class="card mb-3">
            <nuxt-link to="/buku/buku1">
              <div class="card-body">
                <img src="~/assets/img/cover1.jpg" class="cover" alt="cover 1">
              </div>
            </nuxt-link>
            </div>
          </div>
        <div class="col-lg-2">
          <div class="card mb-3">
            <nuxt-link to="/buku/buku2">
            <div class="card-body">
              <img src="~/assets/img/cover2.jpeg" class="cover" alt="cover 2">
            </div>
            </nuxt-link>
          </div>
        </div>
        <div class="col-lg-2">
          <div class="card mb-3">
            <nuxt-link to="/buku/buku3">
            <div class="card-body">
              <img src="~/assets/img/cover3.jpg" class="cover" alt="cover 3">
            </div>
            </nuxt-link>
          </div>
        </div>
        <div class="col-lg-2">
          <div class="card mb-3">
            <nuxt-link to="/buku/buku4">
            <div class="card-body">
              <img src="~/assets/img/cover4.jpg" class="cover" alt="cover 4">
            </div>
            </nuxt-link>
          </div>
        </div>
      </div>
      </div>
    </div>
  </div>
  <nuxt-link to="../">
    <button type="submit" class="btn btn-secondary btn-lg rounded-5 px-5" style="margin-left: 90.5%;">KEMBALI</button>
  </nuxt-link>
</template>

<style scoped>
.card-body {
  width: 100%;
  /*height: 20em; */
  padding: 0;
}
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}
</style>