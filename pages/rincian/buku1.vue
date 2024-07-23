<template>
  <div class="container">
    <div class="row mt-4 d-flex justify-content-evenly">
      <div class="col-lg-4">
        <div class="card">
          <div class="card-body">
            <img src="~/assets/img/cover1.jpg" width="220px" height="340px" class="cover" alt="cover1" />
          </div>
        </div>
      </div>
      <div class="col-4">
        <p>penerbit:sunankalijaga</p>
        <p>isbn:978-623-6155-83-7</p>
        <p>penulis:achmad chodjim</p>
      </div>
    </div>
    <div class="row mt-5">
      <h2>sunankalijaga</h2>
      <p class="mt-3">
        Sunan Kalijaga lahir pada tahun 1450 Masehi dari pasangan bangsawan Tuban, yaitu Tumenggung Wilatikta bupati Tuban saat itu dan Dewi Nawangrum. Karena darah bangsawan miliknya, Sunan Kalijaga kecil diberi gelar sebagai Raden Mas Syahid dalam
        beberapa literatur disebut Raden Mas Said
      </p>
    </div>

    <NuxtLink to="/buku">
      <button type="button" class="btn btn-primary">kembali</button>
    </NuxtLink>
  </div>
</template>

<style scoped>
.cover {
  width: 255px;
  height: 370px;
  box-shadow: 1px 10px 50px rgb(0, 0, 0, 0.5);
}
.card {
  border: none !important;
}
</style>
