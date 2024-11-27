<!-- eslint-disable no-unused-vars -->
<script setup>
import { ref, computed } from 'vue'
import books from './bookdata.js'
const isCard = ref(true)
console.log(books)
</script>

<template>
  <div class="container">
    <button v-on:click="isCard = !isCard" class="btn btn-primary">
      <span v-if="isCard">Table</span>
      <span v-else>Card</span>
    </button>

    <table v-if="!isCard" class="table">
      <thead>
        <tr>
          <th scope="col">author</th>
          <th scope="col">title</th>
          <th scope="col">description</th>
          <th scope="col">image</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(book, index) in books" :key="index">
          <td>{{ book.author }}</td>
          <td>{{ book.title }}</td>
          <td>{{ book.description }}</td>
          <td><img :src="book.img_url" height="40em" alt="" /></td>
        </tr>
      </tbody>
    </table>

    <div class="row g-2" v-if="isCard">
      <div class="col-4" v-for="(book, index) in books" :key="index">
        <div class="card">
          <div class="card-body">
            <img :src="book.img_url" class="card-img-top" alt="..." />

            <h5 class="card-title">{{ book.title }}</h5>
            <h6 class="card-subtitle mb-2 text-body-secondary">{{ book.author }}</h6>
            <p class="card-text">{{ book.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style></style>
