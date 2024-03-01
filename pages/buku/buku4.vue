<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-2">
        <div class="card mb-3">
          <div class="card-body">
            <img src="~/assets/img/the-magicians-nephew.jpg" class="the-magicians-nephew" alt="the-magicians-nephew"> 
          </div>
        </div>
      </div>
      <div class="col-lg-6">
      <div class="col p-5"><h1 style="font-size: 40px;">THE MAGICIAN'S NEPHEW</h1></div>
      <h4>Penulis: Clive Staples Lewis</h4>
      <h4>Tahun Terbit: 2022</h4>
      <h4>Deskripsi: Petualangan dimulai! Narnia… tanah tempat para Hewan yang Bisa Bicara tinggal… tempat sang penyihir menunggu… dan dunia yang baru akan terbentuk. 
          Dalam petualangan untuk menyelamatkan seseorang, dua sahabat dipaksa masuk ke dunia lain, tempat seorang penyihir jahat berniat memperbudak mereka.
          Tetapi, Aslan Sang Singa menyanyikan lagu yang membuat tanah baru tercipta, tanah yang di kemudian hari dikenal sebagai Narnia. 
          Dan di Narnia, segala hal mungkin terjadi…</h4>
    </div>
    <nuxt-link to="../">
      <button type="button" class="btn btn-secondary btn-lg rounded-5 px-5" style="margin-left: 90.5%;">KEMBALI</button>
    </nuxt-link>
  </div>
  </div>
</template>

<style scoped>
.cover {
  height: 300px;
  width: 200px;
}
.card.mb-3 {
  margin-top: 50px;
  margin-left: 20px;
  height: 340px;
  width: 235px;
}
h3 {
  margin-top: 60px;
  margin-left: 20px;
}
img {
  height: 300px;
  width: 200px;
}
</style>