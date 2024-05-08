<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12">
        <h2 class="text-center my-4">ISI KUNJUNGAN BUKU</h2>
        <form @submit.prevent="kirimData">
          <div class="mb-3">
            <input v-model="form.nama" type="text"  class= "form-control form-control-lg rounded-5" placeholder="NAMA...">
          </div>
          <div class="mb-3">
            <select v-model="form.keanggotaan" class="form-control form-control-lg form-select rounded-5">
              <option value="">KEANGGOTAAN</option>
              <option v-for="(member, i) in members " :key="i" :value="member.id">{{ member.nama }}
              </option>
            </select>
          </div>
            <div class="mb-3" v-if="form.keanggotaan == '1'">
              <div class="mb-3">
              <select v-model="form.kelas" class="form-control form-control-lg form-select rounded-5">
                <option value="">KELAS</option>
                <option value="">X</option>
                <option value="">XI</option>
                <option value="">XII</option>
              </select>
            </div>
            </div>

            <div class="mb-3">
              <select v-model="form.keperluan" class="form-control form-control-lg form-select rounded-5">
                <option value="">KEPERLUAN</option>
                <option v-for="(item, i) in objectives" :key="i" :value="item.id">{{  item.nama }}</option>

              </select>
            </div>
              <div class="row">
              <div class="col-8">
                <button type="submit" class="btn btn-primary btn-lg rounded-5 px-5">KIRIM</button></div>
              <div class="col-2"><nuxt-link to=".."><button type="button" class="btn btn-secondary btn-lg rounded-5 px-5" style="margin-left: 80.2;">KEMBALI</button></nuxt-link></div>
                </div>
              </form>
            </div>
          </div>
        </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const members = ref([])
const objectives = ref([])

const form = ref({
  nama: "",
  keanggotaan: "",
  kelas: "",
  keperluan: "",
});

const kirimData = async () => {
  console.log (form.value)
  const { error } = await supabase.from('pengunjung').insert([form.value])
  if(!error) navigateTo('/pengunjung')
}

const getKeanggotaan = async () => {
  const { data, error } = await supabase.from('keanggotaan').select('*')
  if(data) members.value = data
}

const getKeperluan = async () => {
  const { data, error } = await supabase.from('keperluan').select('*')
  if(data) objectives.value = data
}

onMounted(() => {
  getKeanggotaan()
  getKeperluan()
})

</script>