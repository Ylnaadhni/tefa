<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <div class="my-3">
          <form @submit.prevent="getBooks">
            <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?">
          </form>
        </div>
        <div class="my-3 text-muted">Menampilkan 5 dari 5</div>
        <div class="row">
          <div v-for="(book, i) in books" :key="i" class="col-lg-2">
            <div class="card mb-3">
              <nuxt-link :to="`/buku/${book.id}`">
                <div class="card-body">
                <img :src="book.cover" class="cover" alt="cover 1">
                </div>
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
      <nuxt-link to="../">
        <button type="button" class="btn btn-secondary btn-lg rounded-5 px-5" style="margin-left: 90.5%;">KEMBALI</button>
      </nuxt-link>
    </div>
  </div>
</template>

<script setup>
useHead({title: 'perpus digital yuliana',
meta:[{name: 'description', content:'aplikasi kunjungan dan pencarian buku perpus SMKN 4 tsm'}]
})
const supabase = useSupabaseClient()

const books = ref([])
const keyword = ref('')

const getBooks = async () => {
  const { data, error } = await supabase.from('buku').select('*, kategori(*)')
  .ilike('judul', `%${keyword.value}%`)
  if(data) books.value = data
}

onMounted(() => {
  getBooks()
})
</script>

<style scoped>
.card-body {
  width: 100%;
  height: 400px;
  padding: 0;
}
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}
</style>