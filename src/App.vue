<script setup>
import { ref, onMounted } from 'vue'

const products = ref([])
const error = ref(null)

const formatPrice = (price) => {
  return new Intl.NumberFormat('vi-VN').format(price)
}

onMounted(async () => {
  try {
    const res = await fetch('http://localhost:3000/products')
    if (!res.ok) {
      throw new Error('Không thể tải dữ liệu sản phẩm')
    }
    products.value = await res.json()
  } catch (e) {
    error.value = e.message
    console.error('Error:', e)
  }
})
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img style="height: 70px;"
          src="https://upload.wikimedia.org/wikipedia/vi/thumb/3/37/Bitis_logo.svg/1200px-Bitis_logo.svg.png" alt="">
      </a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavDropdown"
        aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">VỀ BITI'S
            </a>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button"
              data-bs-toggle="dropdown" aria-expanded="false">
              Nam
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li><a class="dropdown-item" href="#">Action</a></li>
              <li><a class="dropdown-item" href="#">Another action</a></li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button"
              data-bs-toggle="dropdown" aria-expanded="false">
              Nữ
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li><a class="dropdown-item" href="#">Action</a></li>
              <li><a class="dropdown-item" href="#">Another action</a></li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button"
              data-bs-toggle="dropdown" aria-expanded="false">
              bé trai
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li><a class="dropdown-item" href="#">Action</a></li>
              <li><a class="dropdown-item" href="#">Another action</a></li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button"
              data-bs-toggle="dropdown" aria-expanded="false">
              bé gái
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li><a class="dropdown-item" href="#">Action</a></li>
              <li><a class="dropdown-item" href="#">Another action</a></li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button"
              data-bs-toggle="dropdown" aria-expanded="false">
              phụ kiện
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li><a class="dropdown-item" href="#">Action</a></li>
              <li><a class="dropdown-item" href="#">Another action</a></li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button"
              data-bs-toggle="dropdown" aria-expanded="false">
              Mới & RESTOCK
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li><a class="dropdown-item" href="#">Action</a></li>
              <li><a class="dropdown-item" href="#">Another action</a></li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button"
              data-bs-toggle="dropdown" aria-expanded="false">
              Chia sẻ
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <li><a class="dropdown-item" href="#">Action</a></li>
              <li><a class="dropdown-item" href="#">Another action</a></li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
        </ul>
        <div class="d-flex ms-auto align-items-center gap-3">
          <a href="#" class="text-dark"><i class="bi bi-search fs-5"></i></a>
          <a href="#" class="text-dark"><i class="bi bi-person fs-5"></i></a>
          <a href="#" class="text-dark"><i class="bi bi-bag-dash fs-5"></i></a>
          <a href="#" class="text-dark"><i class="bi bi-heart fs-5"></i></a>
        </div>

      </div>
    </div>
  </nav>
  <section class="bg-light py-1">
    <div class="container">
      <img style="width: 100%;"
        src="https://file.hstatic.net/1000230642/collection/banner_running_87aa1e3371a14b78aaa452f9e8ffbb39.jpg" alt="">
    </div>
  </section>
  <div class="container my-5">
    <div class="row">
      <div class="col-md-3 mb-4" v-for="product in products" :key="product.id">
        <div class="card h-100 shadow-sm">
            <button href="#" class="text-dark tuy-chinh-tim">
              <i class="bi bi-heart fs-5"></i>
            </button>
          <img :src="product.image" class="card-img-top" :alt="product.name">
          <div class="card-body d-flex flex-column">
            <h5 class="card-title">{{ product.name }}</h5>
            <div class="thong-so">
              <p class="card-title">số lượng size: {{ product.size }}</p>
              <p class="card-title">số lượng màu sắc: {{ product.color }}</p>
            </div>
            <p class="card-text text-muted">{{ product.description }}</p>
            <div class="mt-auto d-flex justify-content-between align-items-center">
              <span class="text fs-5">{{ formatPrice(product.price) }}₫</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.tuy-chinh-tim{
  position: absolute;
  top: 10px;
  right: 10px;
  border: none;
  background-color: none;
}
.thong-so
{
  display: flex;
  justify-content: space-between;
}
.thong-so > p{
  font-size: 10px;
}
</style>
