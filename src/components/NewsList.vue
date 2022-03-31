<template>
 
 <div id="articlesparent">
    <div v-for= "article in articles" class="card" style="width: 18rem;">
        <img class="card-img-top" v-bind:src=article.urlToImage alt="Card image cap">
        <div class="card-body">
            <h5 class="card-title">{{ article.title }}</h5>
            <p class="card-text">{{article.description}}</p>
        </div>
    </div>
</div>
</template>
<script>
export default {
 data() {
 return {
    articles: []
 };
 },
 created() {
     let self = this;
    fetch('https://newsapi.org/v2/top-headlines?country=us',
    {
        headers: {
            'Authorization': `Bearer 85c0b0940af649688c9dc2455f8ee68e`
        }
    })
    .then(function(response) {
        return response.json();
    })
    .then(function(data) {
        console.log(data);
        self.articles = data.articles;
    });
}
};
</script>