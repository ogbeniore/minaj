<template>
    <div>
        <p class="main-intro">
            <span class="line-1">Happy anniversary, my love.</span>
            <span class="line-2">
                Another year has flown by, and I cannot believe how lucky we are to have each other 🎉
            </span>
        </p>
        <div class="year-grid">
            <div class="year-item" v-for="year in covers" :key="year.name">
                <nuxt-link :to="`/year/${year.name}`">
                    <div class="year-item-image">
                        <img :src="year.image" :alt="year.name">
                    </div>
                    <span class="year-item-name">{{ year.name }}</span>
                </nuxt-link>
            </div>
        </div>
    </div>
</template>

<script>
import Vue  from 'vue';

export default Vue.extend({
    data: () => ({
        covers: [
            {
                name: '01',
                image: 'https://res.cloudinary.com/plushdeveloper/image/upload/v1674470776/minaj/IMG_5231.webp'
            },
            {
                name: '02',
                image: 'https://res.cloudinary.com/plushdeveloper/image/upload/v1674470776/minaj/IMG_2575.webp'
            },
            {
                name: '03',
                image: 'https://res.cloudinary.com/plushdeveloper/image/upload/v1674470776/minaj/PXL_20221225_110314443.webp'
            }
        ]
    })
})
</script>

<style lang="scss" scoped>
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
        &.line-1 {
            animation: fadeIn 500ms ease-in-out forwards;
        }
        &.line-2 {
            animation: fadeInUp 500ms 300ms ease-in-out forwards;
        }
    }

    @media screen and (max-width: 768px) {
        font-size: 24px;
        line-height: 30px;
    }
}

.year-grid {
    display: grid;
    grid-template-columns: repeat(3, 200px);
    grid-gap: 60px;
    justify-content: center;
    align-items: center;
    @media screen and (max-width: 768px) {
        grid-template-columns: repeat(1, 200px);

    }
    .year-item {
        height: 400px;
        animation: fader 300ms ease-out forwards;
        opacity: 0;
        position: relative;
        cursor: pointer;
        &-image {
            border-radius: 80px;
            overflow: hidden;
            height: 100%;

            img {
                width: auto;
                height: 100%;
                object-fit: contain;
                filter: grayscale(1);
                transition: all 300ms;
            }

            &::before {
                height: 100%;
                width: 100%;
                content: "";
                background-color: rgba(#ed008c, 0.3);
                display: block;
                position: absolute;
                z-index: 1;
                border-radius: 80px;
                opacity: 1;
                transition: all 100ms;
            }
        }
        &:hover {
            img {
                filter: grayscale(0);
                transform: scale(1.5);
            }
            .year-item-image::before {
                opacity: 0;
            }
        }

        @for $i from 1 through 3 {
        &:nth-child(#{$i}) {
            animation-delay: 700ms + (100ms * $i);
        }
        }

        &-name {
            font-family: 'Rubik Gemstones', serif;
            font-weight: 700;
            font-size: 60px;
            position: absolute;
            color: #ffffff;
            bottom: 0;
            right: 50%;
            transform: translateX(50%);
            z-index: 2;
        }
    }
}

@keyframes fader {

    from {
        opacity: 0.2;
        transform: translateY(-10%);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
    
}

@keyframes fadeIn {

    from {
        opacity: 0.2;
        transform: translateY(-100%);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
    
}
@keyframes fadeInUp {

    from {
        opacity: 0.2;
        transform: translateY(50%);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
    
}
</style>