<template>
    <div class="main" v-if="isLoaded && pageData">
        <div class="page-name">
            <nuxt-link to="/year/01" :class="{active: pageData.name == '01'}">01</nuxt-link>
            <nuxt-link to="/year/02" :class="{active: pageData.name == '02'}">02</nuxt-link>
            <nuxt-link to="/year/03" :class="{active: pageData.name == '03'}">03</nuxt-link>
        </div>
        <nuxt-link to="/" class="home">Home</nuxt-link>
        <p class="main-intro">
            <span class="line-1" v-html="pageData.heroText"></span>
        </p>
        <div class="image-gallery">
            <div class="gallery-item" v-for="(image, index) in pageData.images" :key="index">
                <img :src="image.url" :alt="image.caption">
                <span class="gallery-item-caption">
                    {{ image.caption }}
                </span>
            </div>
        </div>
        <p class="main-intro">
            <span v-html="pageData.bottomLine"></span>
        </p>
    </div>
</template>

<script>
import Vue from 'vue';
import allData from '../../data/years.json';
export default Vue.extend({
    data: () => ({
        id: 'lol',
        pageData: null,
        isLoaded: false

    }),
    mounted() {
        this.$nextTick(() => {
        this.$nuxt.$loading.start()
        setTimeout(() => {
            this.$nuxt.$loading.finish()
            this.isLoaded = true
        }, 700)
        })
        this.id = this.$route.params.id
        this.pageData = allData.find(year => year.name === this.id)
      },
})
</script>

<style lang="scss" scoped>
.main {
    max-width: 1300px;
    margin: 0 auto;
}
.main-intro {
    margin: auto;
    text-align: center;
    max-width: 800px;
    font-size: 40px;
    font-weight: 600;
    line-height: 60px;
    min-height: 240px;
    color: #ed008c;
    font-family: 'Dancing Script', cursive;
    padding-top: 80px;
    padding-bottom: 60px;
    span {
        display: block;
        opacity: 0;
        animation: fadeIn 500ms ease-in-out forwards;
    }
    @media screen and (max-width: 768px) {
        font-size: 24px;
        line-height: 30px;
    }
}

.home {
    font-family: 'Rubik Gemstones', serif;
    font-weight: 700;
    font-size: 30px;
    position: fixed;
    color: #ed008c;
    top: 40px;
    left: 40px;
    z-index: 3;
}

.page-name {
    font-family: 'Rubik Gemstones', serif;
    font-weight: 700;
    font-size: 120px;
    position: fixed;
    color: #ed008c;
    top: 80px;
    left: 40px;
    z-index: 3;
    a {
        opacity: 0.5;
        display: block;
        color: inherit;
        &.active {
            opacity: 1;
        }
    }
}
@keyframes fadeIn {

    from {
        opacity: 0.2;
        transform: translateY(10%);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
    
}

.image-gallery {
    padding: 0 100px;
    display: grid;
    grid-template-columns: repeat(2, 45%);
    grid-gap: 40px;
    justify-content: space-between;

    .gallery-item {
        // background-color: rgba($color: #ed008c, $alpha: 0.7);
        height: 500px;
        padding: 10px;
        border-radius: 10px;
        display: flex;
        position: relative;

        img {
            box-shadow: 2px 4px 2px rgba($color: #ed008c, $alpha: 0.3);
            margin: auto;
            height: 90%;
            width: auto;
            object-fit: contain;
        }

        &-caption {
            position: absolute;
            bottom: 0;
            right: 50%;
            transform: translateX(50%);
            font-style: italic;
        }
    }
}
</style>