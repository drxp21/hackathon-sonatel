<template>
    <div class="container">
        <h1 class="title">Réflexions sur l'Évangile du Jour</h1>
        <div class="gospel-section">
            <h2 class="gospel-title">L'Évangile d'aujourd'hui</h2>
            <p class="gospel-text">
                <em>
                    « Jésus dit : "Moi, je suis le chemin, la vérité et la vie ; personne ne vient au Père sans passer par
                    moi." »
                    <br />
                    (Jean 14:6)
                </em>
            </p>
        </div>
        <div class="comments-section">
            <h2 class="comments-title">Commentaires des religieux</h2>
            <div v-for="(comment, index) in religiousComments" :key="index" class="comment-card">
                <h3 class="comment-author">✝ {{ comment.author }}</h3>
                <p class="comment-text">« {{ comment.text }} »</p>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            religiousComments: [
                {
                    author: "Saint Augustin",
                    text: "Suivre Jésus, c'est marcher sur le chemin de la vérité, en acceptant qu'il nous guide dans chaque étape de notre vie.",
                },
                {
                    author: "Saint Thomas d'Aquin",
                    text: "Le Christ est la vérité parfaite, car en lui réside toute sagesse et toute connaissance nécessaires pour atteindre le Père.",
                },
                {
                    author: "Pape François",
                    text: "Dans ce passage, Jésus nous rappelle que la foi n'est pas une simple connaissance, mais une relation vivante avec lui.",
                },
                {
                    author: "Sainte Thérèse de Lisieux",
                    text: "Se confier à Jésus, c'est accepter d'aimer sans condition, même dans les moments d'incertitude.",
                },
            ],
        };
    },
};
</script>
  
<style scoped>
.container {
    padding: 2rem;
    max-width: 800px;
    margin: 0 auto;
    background-color: #fdfdfd;
    /* Couleur claire pour le fond */
    color: #333;
    /* Texte sombre */
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.title {
    text-align: center;
    font-size: 2rem;
    margin-bottom: 2rem;
    color: #222;
    /* Couleur sombre pour le titre */
}

.gospel-section {
    background-color: #fff;
    /* Blanc pour le fond */
    padding: 1.5rem;
    border: 1px solid #ddd;
    /* Bordure légère */
    border-radius: 8px;
    margin-bottom: 2rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
    /* Ombre légère */
}

.gospel-title {
    font-size: 1.5rem;
    margin-bottom: 1rem;
    color: #444;
    /* Couleur légèrement sombre */
}

.gospel-text {
    font-size: 1.2rem;
    line-height: 1.6;
    text-align: justify;
}

.comments-section {
    background-color: #fff;
    /* Blanc pour le fond */
    padding: 1.5rem;
    border: 1px solid #ddd;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
    /* Ombre légère */
}

.comments-title {
    font-size: 1.5rem;
    margin-bottom: 1rem;
    color: #444;
}

.comment-card {
    margin-bottom: 1.5rem;
    padding: 1rem;
    border-left: 4px solid #007bff;
    /* Couleur bleu clair pour indiquer une importance */
    background-color: #f8f9fa;
    /* Gris très clair */
    border-radius: 4px;
}

.comment-author {
    font-size: 1.2rem;
    color: #007bff;
    /* Bleu clair pour les auteurs */
    margin-bottom: 0.5rem;
}

.comment-text {
    font-size: 1rem;
    line-height: 1.5;
    text-align: justify;
    color: #555;
    /* Texte légèrement plus sombre */
}</style>
  