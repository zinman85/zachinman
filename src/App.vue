<template>
    <v-app>
        <v-app-bar app dark>
            <v-toolbar-title>Vuetify Dashboard</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn
                v-for="link in links"
                :key="`${link.label}-header-link`"
                text
                rounded
                class="my-2"
                @click="$vuetify.goTo(link.url)"
            >{{ link.label }}</v-btn>
        </v-app-bar>
        <v-content>
            <!-- Content Here -->
            <About id="about" :class="compoenetStyle" />
            <Experience id="experience" style="min-height: 600px;" />
            <Portfolio id="portfolio" style="height: 600px;" />
            <Contact id="contact" style="height: 600px;" />
        </v-content>
    </v-app>
</template>

<script>
import About from "./components/About.vue";
import Experience from "./components/Experience.vue";
import Portfolio from "./components/Portfolio.vue";
import Contact from "./components/Contact.vue";

export default {
    name: "App",

    components: {
        About,
        Experience,
        Portfolio,
        Contact
    },

    data: () => ({
        compoenetStyle: {
            "min-height": window.innerHeight
        },
        minHeight: 0,
        duration: 300,
        offset: 0,
        easing: "easeInOutCubic",
        links: [
            {
                label: "About",
                url: "#about"
            },
            {
                label: "Experience",
                url: "#experience"
            },
            {
                label: "Portfolio",
                url: "#portfolio"
            },
            {
                label: "Contact",
                url: "#contact"
            },
            {
                label: "Resume",
                url: "#"
            }
        ]
    }),
    created() {
        this.minHeight = window.innerHeight;
    },
    computed: {
        options() {
            return {
                duration: this.duration,
                offset: this.offset,
                easing: this.easing
            };
        }
    }
};
</script>

<style>
</style>
