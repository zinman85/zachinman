<template>
    <div>
        <v-app-bar app flat color="transparent">
            <v-toolbar-title class="hidden-sm-and-down">
                <v-btn text class="display-2" @click="navigateTo(linkHeader.url)">ZI</v-btn>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-app-bar-nav-icon large @click.stop="drawer = !drawer" class="hidden-md-and-up"></v-app-bar-nav-icon>
            <v-btn
                v-for="link in links"
                :key="`${link.label}-header-link`"
                text
                class="my-2 hidden-sm-and-down"
                @click="navigateTo(link.url)"
            >{{ link.label }}</v-btn>
        </v-app-bar>
        <v-navigation-drawer v-model="drawer" fixed temporary>
            <v-list nav>
                <v-list-item>
                    <v-list-item-content>
                        <v-list-item-title>
                            <v-btn text class="display-2" @click="navigateTo(linkHeader.url)">ZI</v-btn>
                        </v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
                <v-list-item v-for="link in links" :key="`${link.label}-drawer-link`">
                    <v-btn text @click="navigateTo(link.url)">{{ link.label }}</v-btn>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
    </div>
</template>

<script>
export default {
    data: () => ({
        duration: 300,
        drawer: false,
        easing: "easeInOutCubic",
        linkHeader: {
            label: "Header",
            url: "#header"
        },
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
        ],
        offset: 0
    }),
    computed: {
        options() {
            return {
                duration: this.duration,
                offset: this.offset,
                easing: this.easing
            };
        }
    },
    methods: {
        navigateTo(linkTo) {
            this.$vuetify.goTo(linkTo, this.options);
            if (this.$vuetify.breakpoint.smAndDown) {
                this.drawer = false;
            }
            return;
        }
    }
};
</script>

<style scoped>
/* Removes background effect */
.v-btn:before {
    background-color: transparent;
}

.v-btn--click {
    background-color: transparent;
}

.v-btn--active {
    color: blue;
}

.v-btn:hover {
    color: #e53411;
}
</style>
