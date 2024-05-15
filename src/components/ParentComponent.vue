<template>
  <div>
    <h1 class="my-4">Daftar Buku</h1>
    <form @submit.prevent="addBook" class="mb-4">
      <div class="form-row">
        <div class="col">
          <input v-model="newBook.title" type="text" class="form-control" placeholder="Judul Buku" required>
        </div>
        <div class="col">
          <input v-model="newBook.author" type="text" class="form-control" placeholder="Penulis Buku" required>
        </div>
        <div class="col">
          <input v-model="newBook.description" type="text" class="form-control" placeholder="Deskripsi Buku" required>
        </div>
        <div class="col">
          <input v-model="newBook.cover" type="text" class="form-control" placeholder="URL Sampul Buku" required>
        </div>
        <div class="col">
          <button type="submit" class="btn btn-primary">Tambah Buku</button>
        </div>
      </div>
    </form>
    <BookList :books="books" @book-selected="displayBookDetail">
      <template #header>
        <h2 class="mb-3">Silakan pilih buku:</h2>
      </template>
    </BookList>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import BookList from './BookList.vue';
import Swal from 'sweetalert2';

const books = ref([
  { id: 1, title: 'To Kill a Mockingbird', author: 'Harper Lee', description: 'Novel klasik yang menceritakan tentang keadilan, rasisme, dan kehidupan di Alabama selatan pada tahun 1930-an', cover: 'https://books.google.co.id/books/publisher/content?id=_LyTCgAAQBAJ&hl=id&pg=PP1&img=1&zoom=3&bul=1&sig=ACfU3U2PDUkjLubxyTF74uFMhClFwC_0nQ&w=1280' },
  { id: 2, title: 'Laskar Pelangi', author: 'Andrea Hirata', description: 'Novel ini mengisahkan perjuangan sekelompok anak muda dari Belitung dalam menghadapi tantangan hidup dan mencari ilmu di tengah keterbatasan sosial dan ekonomi.', cover: 'https://cdn1-production-images-kly.akamaized.net/2OyyYub9tFxD7bMTAxBELSixX9g=/469x625/smart/filters:quality(75):strip_icc():format(webp)/kly-media-production/medias/3455812/original/026174800_1620899775-Laskar_Pelangi_0.jpg' },
  { id: 3, title: 'Beauty is a Wound (Cantik Itu Luka)', author: 'Eka Kurniawan', description: 'Novel epik yang menampilkan berbagai aspek sejarah, mitologi, dan budaya Indonesia, dengan sentuhan magis-realis yang kuat', cover: 'https://books.google.co.id/books/content?id=-VWFJ00mffUC&hl=id&pg=PP1&img=1&zoom=3&bul=1&sig=ACfU3U2OzLUIS3XseDaxe1YNWjpHGCg0HQ&w=1280' },
]);

const newBook = ref({
  title: '',
  author: '',
  description: '',
  cover: ''
});

const selectedBook = ref(null);

function displayBookDetail(book) {
  Swal.fire({
    title: book.title,
    html: `<p><strong>Penulis:</strong> ${book.author}</p>
      <p>${book.description}</p>`,
    imageUrl: book.cover,
    imageWidth: 150,
    imageHeight: 150,
    imageAlt: book.title
  });
}

function addBook() {
  const book = { ...newBook.value, id: books.value.length + 1 };
  books.value.push(book);
  newBook.value = { title: '', author: '', description: '', cover: '' };
}
</script>

<style scoped>
h1 {
  color: white;
  font-weight: bold;
}
.col{
  margin-top: 10px;
  width: 50%;
  backdrop-filter: blur(5px);
}
.col input{
  border: 1px solid white;
  background-color: transparent;
}
.col input::placeholder{
  color: white;
}
</style>
