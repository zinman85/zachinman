<template>
    <v-app>
        <NavBar />
        <v-content>
            <v-container>
                <Header id="header" :style="{'min-height': `${window.height}px`}" />
                <About id="about" :style="{'min-height': `${window.height}px`}" />
                <Experience id="experience" :style="{'min-height': `${window.height}px`}" />
                <Portfolio id="portfolio" :style="{'min-height': `${window.height}px`}" />
                <Contact id="contact" :style="{'min-height': `${window.height}px`}" />
            </v-container>
        </v-content>
    </v-app>
</template>

<script>
import About from "./views/About";
import Contact from "./views/Contact";
import Experience from "./views/Experience";
import Header from "./views/Header";
import NavBar from "./components/NavBar";
import Portfolio from "./views/Portfolio";

export default {
    name: "App",
    components: {
        About,
        Contact,
        Experience,
        Header,
        NavBar,
        Portfolio
    },
    data: () => ({
        window: {
            width: 0,
            height: 600
        }
    }),
    created() {
        window.addEventListener("resize", this.handleResize);
        this.handleResize();
    },
    destroyed() {
        window.removeEventListener("resize", this.handleResize);
    },
    methods: {
        handleResize() {
            this.window.width = window.innerWidth;
            this.window.height = window.innerHeight;
        }
    }
};
</script>

<style>
/* html {
        background: rgba(0, 0, 0, 0);
    } */
</style>
