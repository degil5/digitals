<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">BUKU</h2>
        <div class="my-3">
          <form @submit.prevent="getBooks">
            <input type="search" class="from-control rounded-5" placeholder="Mau baca apa hari ini?" />
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan 3 dari 3</div>
        <div class="row justify-content-evenly">
          <div v-for="(book, i) in books" :key="i" class="col-sm-3 m-1">
            <nuxt-link :to="`/buku/${book.id}`">
              <div class="card" style="width: 18rem;">
                <img :src="book.cover" class="card-img-top" :alt="book.judul">
                <div class="card-body">
                  <p class="card-text">{{ book.judul }}</p>
                </div>
              </div>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
    <NuxtLink to="/">
      <button type="button" class="btn btn-primary">kembali</button>
    </NuxtLink>
  </div>
</template>

<style scoped>
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}
</style>

<script setup>
const supabase = useSupabaseClient()

const books = ref([])
const keyword = ref('')

const getBooks = async () => {
  const { data, error } = await supabase.from('buku').select(`*`)
    .ilike(`judul`, `%${keyword.value}`)
  if (data) books.value = data
}

onMounted(() => {
  getBooks()
})
</script>
