<template>
    <v-app id="inspire">
        <v-app-bar app color="white" flat>
            <v-container class="py-0 fill-height">
                <v-avatar class="mr-10" color="grey darken-1" size="32"></v-avatar>

                <v-btn v-for="link in links" :key="link" text>
                    {{ link }}
                </v-btn>

                <v-spacer></v-spacer>

                <v-responsive max-width="260">
                    <v-text-field
                        dense
                        flat
                        hide-details
                        rounded
                        solo-inverted
                    ></v-text-field>
                </v-responsive>
            </v-container>
        </v-app-bar>

        <v-main class="grey lighten-3">
            <v-container>
                <v-row>
                    <v-col cols="2">
                        <v-sheet rounded="lg">
                            <v-list color="transparent">
                                <v-list-item @click="onClickMenu(n)"
                                    v-for="n in menus" :key="n" link>
                                    <v-list-item-content>
                                        <v-list-item-title>
                                            {{ n }}
                                        </v-list-item-title>
                                    </v-list-item-content>
                                </v-list-item>

                                <v-divider class="my-2"></v-divider>

                                <v-list-item link color="grey lighten-4">
                                    <v-list-item-content>
                                        <v-list-item-title>
                                            Refresh
                                        </v-list-item-title>
                                    </v-list-item-content>
                                </v-list-item>
                            </v-list>
                        </v-sheet>
                    </v-col>

                    <v-col>
                        <v-sheet style="padding: 1rem;" min-height="70vh" rounded="lg">
<!--                            <div class="text-h2">{{selectedMenu}}</div>-->
<!--                            <br>-->
                            <div :is="selectedMenu"></div>
                        </v-sheet>
                    </v-col>
                </v-row>
            </v-container>
        </v-main>
    </v-app>
</template>

<script>
    'use strict';
    import GridLayoutSystem from './components/GridLayoutSystem';
    import Cote from './components/Cote';
    import Font from './components/Font';
    import Button from './components/Button';

    const components = {
        GridLayoutSystem,
        Cote,
        Font,
        Button
    };
    const menus = Object.keys(components).filter((v) => {
        return ! v.startsWith('V')
    });
    export default {
        name: 'App',
        components: components,
        data: () => ({
            links: [
                'Dashboard',
                'Messages',
                'Profile',
                'Updates',
            ],
            selectedMenu: menus[0],
            menus: menus
        }),
        methods: {
            onClickMenu: function (menu) {
                this.selectedMenu = menu;
            }
        }
    };
</script>
