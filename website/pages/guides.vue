 <!-- Component Template 1.2 -->
   <!-- ----------------------------------------------------------------------
  --------- SCRIPTS
  ----------------------------------------------------------------------- -->
<script>
const name = 'guides'
export default {
    name: name,
    layout: 'default',
    //   layout: 'default',
    data() {
        return {
            activeArticle: '',
        };

    },
    methods: {
        formatDate(date) {
            const options = { year: 'numeric', month: 'long', day: 'numeric' }
            return new Date(date).toLocaleDateString('en', options)
        },
        selectArticle(title) {
            if (title != this.activeArticle) {
                // console.log(this.activeArticle)
                this.activeArticle = title;
                // this.$refs["navigation"].scrollIntoView({ behavior: "smooth" });
                // console.log(this.activeArticle)
            }
        },
        scrolltoArticle(title) {
            if (title != this.activeArticle) {
                const element = this.$el.getElementsByClassName(title)[0];
                if (element) {
                    element.scrollIntoView({ behavior: 'smooth' });
                }
                this.activeArticle = title;
                // this.$refs["navigation"].scrollIntoView({ behavior: "smooth" });
                // console.log(this.activeArticle)
            }
        },
    },
    async asyncData({ $content, params }) {
        const articles = await $content(name).sortBy("slug").fetch(); //.sortBy("date", "desc")
        // console.log(activeArticle)
        return {
            articles,
        }
    }
}
</script>
    
     <!-- ----------------------------------------------------------------------
      --------- TEMPLATE
      ----------------------------------------------------------------------- -->
<template>
    <div class="main">
        <div class="article" v-for="(article, index) of articles" :key="article.slug">
            <div v-if="article.draft == false">
                <article @mouseover="selectArticle(article.title)" class="content">
                    <!-- <hr v-if="index != 0"> -->
                    <div class="article-meta">
                        <h1 :class="article.title">{{ article.title }}</h1>
                        <span>Last update: {{ formatDate(article.updatedAt) }}</span>
                    </div>
                    <br>
                    <!-- <p>{{ article.description }}</p> -->
                    <!-- <img :src="article.img" :alt="article.alt" /> -->
                    <nuxt-content :document="article" />
                    <!-- <pre> {{ article }} </pre> -->
                </article>
                <br>
                <br>
                <br>
            </div>
        </div>
        <div class="toc-container">
            <div class="toc" v-for="article of articles" :key="article.slug">
                <div v-if="article.draft == false">
                    <div class="toc-title" @click="scrolltoArticle(article.title)">
                        <span v-if="article.title == activeArticle">-</span>
                        <span v-else>+</span>
                        {{ article.title }}
                    </div>
                    <span v-if="article.title == activeArticle" v-for="link of article.toc" :key="link.id">
                        &emsp; <NuxtLink class="toc-content" :to="`#${link.id}`"> - {{ link.text }}</NuxtLink>
                        <br>
                    </span>
                    <br>
                </div>
            </div>
        </div>
    </div>
</template>
    
     <!-- ----------------------------------------------------------------------
      --------- STYLES
      ----------------------------------------------------------------------- -->
<style scoped>
@media (max-width: 480px) {
    .article {
        grid-column: 1/11;
    }

    .toc {
        display: none;
    }
}

@media (min-width: 481px) and (max-width: 1024px) {
    .article {
        grid-column: 1/11;
        /* display: flex; */
        /* flex: 1; */
    }

    .toc {
        display: none;
    }
}

@media (min-width: 1025px) {
    .article {
        grid-column: 1/8
    }

    .toc {
        grid-column: 8/11;
        /* border-left: 1px solid #ccc; */
    }
}

.main {
    display: grid;
    grid-template-columns: repeat(10, 1fr);
    grid-column-gap: calc(2 * var(--main-font-size));
    margin-top: calc(.5 * var(--navigation-height));
}

.article .article-meta {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
}

.article -article-meta h1 {
    margin-top: auto;
    margin-bottom: 0;
}

.article .article-meta span {
    margin: auto 0 0 auto;
    opacity: .4;
}

.toc-container {
    position: fixed;
    left: calc(var(--page-width)*1.25);
}

.toc-container * div:hover {
    cursor: pointer;
}

.toc-container .toc-title {
    text-decoration: none;
    color: var(--color-primary);
}

.toc-container .toc-title:hover {
    text-decoration: underline;
}

.toc-container .toc-content {
    text-decoration: none;
    color: var(--color-primary);
}

.toc-container .toc-content:hover {
    text-decoration: underline;
}
</style>
      