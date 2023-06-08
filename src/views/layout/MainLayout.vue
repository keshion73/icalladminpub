<template>
    <v-app>
      
        <Lnb :drawer="drawer">
        </Lnb>
        <v-main>
            <app-bar></app-bar>
            <div class="page-wrap">
                <router-view class="page-cont"></router-view>
            </div>
            <Footer></Footer>
        </v-main>
    </v-app>
</template>
    
<script>
import Header from './Header.vue';
import Lnb from './Lnb.vue';
import Footer from './Footer.vue';

export default {
    components: {
        Header,
        Footer,
        Lnb
    },
    computed: {
    },
    mounted() {
    },
    created() {
    },
    beforeUnmount() {
    },
    data() {
        return {
            drawer: null,
        }
    },
    methods: {
    }
}
</script>
<style lang="scss" scoped>
main::v-deep {
    .v-main__wrap {
        min-height: 100%;
        padding-bottom: 40px;
    }
}
</style>