<template>
    <div class="container">
        <h1 class="title">Livres de la Bible</h1>
        <div class="books-grid">
            <button v-for="book in books" :key="book" class="book-button">
                {{ book }}
            </button>
        </div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            books: [
                "Genèse",
                "Exode",
                "Lévitique",
                "Nombres",
                "Deutéronome",
                "Josué",
                "Juges",
                "Ruth",
                "1 Samuel",
                "2 Samuel",
                "1 Rois",
                "2 Rois",
                "1 Chroniques",
                "2 Chroniques",
                "Esdras",
                "Néhémie",
                "Esther",
                "Job",
                "Psaumes",
                "Proverbes",
                "Ecclésiaste",
                "Cantique des Cantiques",
                "Ésaïe",
                "Jérémie",
                "Lamentations",
                "Ézéchiel",
                "Daniel",
                "Osée",
                "Joël",
                "Amos",
                "Abdias",
                "Jonas",
                "Michée",
                "Nahum",
                "Habacuc",
                "Sophonie",
                "Aggée",
                "Zacharie",
                "Malachie"
            ],
        };
    },

};
</script>
  
<style scoped>
.container {
    text-align: center;
    margin: 2rem;
}

.title {
    font-size: 2rem;
    margin-bottom: 1rem;
}

.books-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    justify-content: center;
}

.book-button {
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 10px 20px;
    cursor: pointer;
    font-size: 1rem;
    transition: background-color 0.3s ease;
}

.book-button:hover {
    background-color: #0056b3;
}
</style>
  