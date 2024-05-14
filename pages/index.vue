<template>
  <div class="container-fluid">
    <div class="row my-5 justify-content-around">
      <div class="col-lg-5">
        <nuxt-link to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-2">
            <div class="card-body">
              <h2 style="font-family: ">Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-5">
        <nuxt-link to="/buku">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2 style="font-family: ">Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>

    <h2 class="mt-5" style="margin-left: 150px;">STATISTIK</h2>
    <div class="row my-5 justify-content-around">
      <div class="col-lg-5">
        <div class="card bg-spengunjung rounded-5">
          <div class="card-body">
              <nuxt-link to="/pengunjung">
                <div class="row">
                <div class="col p-5"><h1 style="font-size: 120px;">{{ jumlahp }}</h1></div>
                <div class="col mt-5 p-5"><h2 style="margin-left: 200px;">Pengunjung</h2></div>
                </div>
              </nuxt-link>
            </div>
          </div>
        </div>

      <div class="col-lg-5">
        <div class="card bg-sbuku rounded-5">
          <div class="card-body">
            <nuxt-link to="./buku">
              <div class="row">
              <div class="col p-5"><h1 style="font-size: 120px; margin-right: 200px">{{ jumlahb }}</h1></div>
              <div class="col mt-5 p-5"><h2 style="font-family: ">Buku</h2></div>
              </div>
            </nuxt-link>
              </div>
              </div>
            </div>
          </div>
          <Chart />
        </div>
</template>

<script setup>

const supabase = useSupabaseClient();
const jumlahp = ref(0);
const jumlahb = ref(0);

async function ambiljumlahp () {
  const { data, error, count } = await supabase
    .from("pengunjung")
    .select("*", {count: "exact"});
  if (count) jumlahp.value = count;
};

async function ambiljumlahb () {
  const { data, error, count } = await supabase
    .from("buku")
    .select("*", {count: "exact"});
  if (count) jumlahb.value = count;
};

onMounted(() => {
  ambiljumlahp();
  ambiljumlahb();
});
</script>

<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px 10px #424242;
}
.card.bg-pengunjung {
  background-image: url("../assets/img/bg-home-kunjungan.jpeg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
}
.card.bg-buku {
  background-image: url("../assets/img/bg-home-cari-buku.jpg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
}
.card.bg-spengunjung {
  background-color: #eaed3f;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
}
.card.bg-sbuku {
  background-color: #a8ffef;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
}
</style>