<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <form @submit.prevent="getPengunjung">
            <input type="search" class="form-control form-control-lg rounded-5" placeholder="fillter..." />
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan 1 dari 1</div>
        <table class="table">
          <thead>
            <tr>
              <td>No</td>
              <td>Nama</td>
              <td>Keanggotaan</td>
              <td>Waktu</td>
              <td>Keperluan</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(visitor, i) in visitors" :key="i">
              <td>{{ i + 1 }}</td>
              <td>{{ visitor.nama }}</td>
              <td>{{ visitor.keanggotaan.nama }}</td>
              <td>{{ visitor.tanggal }}, {{ visitor.waktu }}</td>
              <td>{{ visitor.keperluan.nama }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <NuxtLink to="/">
      <button type="button" class="btn btn-dark bck mt-5">Kembali</button>
    </NuxtLink>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const visitors = ref([])

const getPengunjung = async () => {
  const { data, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
  if (data) visitors.value = data
}


const cariPengunjung = async () => {
  const { data, error } = await supabase.from('pengunjung').select('*, nama(*)')
  if (data) visitors.value = data
}


onMounted(() => {
  getPengunjung()
})
</script>
