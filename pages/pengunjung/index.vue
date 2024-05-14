<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <form @submit.prevent="getpengunjung">
            <input v-model="keyword" type="search" class="form-control form-control-lg rounded-5" placeholder="Filter...">
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan {{ visitors.length }} dari {{ visitors.length }}</div>
        <table class="table">
          <thead>
            <tr>
              <td>#</td>
              <td>NAMA</td>
              <td>KEANGGOTAAN</td>
              <td>WAKTU</td>
              <td>KEPERLUAN</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(visitor,i) in visitors" :key="i">
            <td>{{ i+1 }}.</td>
            <td>{{ visitor.nama }}</td>
            <td>{{ visitor.keanggotaan.nama }}</td>
            <td>{{ visitor.tanggal }}, {{ visitor.waktu }}</td>
            <td>{{ visitor.keperluan.nama }}</td>
            </tr>
          </tbody>
        </table>
        <nuxt-link to="./">
          <button type="submit" class="btn btn-secondary btn-lg rounded-5 px-5" style="margin-left: 80.5%;">KEMBALI</button>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script setup>
useHead({title: 'perpus digital yuliana',
meta:[{name: 'description', content:'selamat mengisi biodata'}]
})
const supabase = useSupabaseClient()
const keyword = ref('')
const visitors = ref([])
const jumlah = ref(0)

const getpengunjung = async () => {
  const { data, error } = await supabase.from('pengunjung').select('*, keanggotaan(*), keperluan(*)')
  .ilike('nama', `%${keyword.value}`)
  .order(`id`, {ascending:false})
  if(data) visitors.value = data
}

const totalPengunjung = async () => {
  const { data, count } = await supabase.from('pengunjung')
  .select("*", { count: 'exact' })
  if (data) jumlah.value = count
}

onMounted(() => {
  getpengunjung()
  totalPengunjung()
})
</script>