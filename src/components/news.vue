<template>
    <ul class="container is-semi-fluid">
        <li v-for="article in articles" :key="article.url" class="notification">
            <article class="media">
                <figure class="media-left">
                    <a :href="article.url" class="image is-128x128" target="_blank">
                    <img :src="article.urlToImage">
                    </a>
                </figure>
                
                <div class="media-content">
                    <div class="content">
                        <p>
                        <strong>{{article.title}}</strong>
                        <br/>
                        {{article.description}}
                        </p>
                    </div>
                    <nav class="level is-mobile">
                        <div class="level-left">
                            <a class="level-item" :href="'https://twitter.com/home?status='+article.url" target="_blank">
                                <span class="icon is-small"><i class="fa fa-retweet"></i></span>
                            </a>
                        </div>
                    </nav>
                </div>
            </article>
        </li>
    </ul>
</template>

<script>
export default{
    name: 'news',
    props: ['articles'],

    data(){
        return {
    
        }
    }
}
</script>

<style>

.is-semi-fluid{
    width:60%;
}

@media (max-width: 850px){
    .is-semi-fluid{
        width:95%;
    }
}
</style>