<template>
<div class="deneme">
  <div class="news-grid" v-if="kartlar && kartlar.length != 0">
    <div class="haber" v-for="i in kartlar">
      <div v-if="i.urlToImage">
        <a :href="i.url">
          <img :src="i.urlToImage" alt="">
          <p>{{i.title}}</p>
        </a>
        <div class="title">
          <p>{{i.source.name}}</p>
        </div>
      </div>
      <div v-else>
        <a :href="i.url">
          <h3>{{i.title}}</h3>
        </a>
      </div>
    </div>
  </div>
    <div v-else>
      <h2>Sonuç Bulunamadı.</h2>
    </div>
  </div>
</template>


<script>
  export default {
    props: [ "kartlar" ]
  }
</script>

<style>
  .haber a {
    text-decoration: none;
  }
  .haber .title {
    text-align: center;
  }
  
  .haber {
    border: 1px solid #ddd;
    padding: 10px;
    border-radius: 8px;
    max-width: 300px;
    transition: all 0.3s ease;
  }

  .haber:hover {
    background-color: #f8f9fa; /* Hover'da arka plan rengi */
    box-shadow: 0 10px 8px rgba(0, 0, 0, 0.1); /* Hover'da gölge efekti */
  }
  .haber img {
    width: 100%;
    height: 200px;
    object-fit: cover; /* Resmin oranını koruyarak kutuya sığmasını sağlar */
    border-radius: 4px;
  }

  .news-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    grid-gap: 20px;
    padding: 20px;
    justify-content: center;
    max-width: 75%;
  }

  .deneme {
    display: flex;
    justify-content: center;
  }
  
  h2 {
    margin-top: 50px;
    text-align: center;
  }

  @media (max-width: 600px) {
    .news-grid {
      grid-template-columns: 1fr; /* Mobil cihazlarda her kart tam genişlikte olacak */
    }
    .haber {
      max-width: none; /* Mobil cihazlarda maksimum genişlik sınırlamasını kaldır */
    }
  }
</style>
