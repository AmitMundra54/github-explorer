<template lang="html">
    <div class="image-fade"
        :id="id"
        :class="className"
        :style="loaded ? {
            backgroundImage: `url('${src}')`,
            opacity: 1,
        } : {}">
    </div>
</template>

<script>
export default {
    data() {
        return {
            img: null,
            loaded: false
        }
    },
    props: ['src', 'className', 'id'],
    mounted() {
        this.$nextTick(() => {
            debugger
            this.loadImg();
        });
    },
    watch: {
        src() {
            this.loadImg();
        }
    },
    methods: {
        loadImg() {
            debugger
            this.loaded = false;
            this.img = new window.Image();
            this.img.onload = () => {
                this.loaded = true;
            };
            this.img.src = this.src;
        }
    }
}
</script>

<style lang="scss">
.image-fade {
    opacity: 0.01;
    transition: opacity 0.5s;
}

</style>
