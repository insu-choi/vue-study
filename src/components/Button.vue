<template>
    <v-row>
        <v-col v-for="item in buttonItems" :key="item" cols="2" align="center" align-self="end" >
            {{item}}
            <br>
            <v-btn v-bind:[item]="true">
                Button
            </v-btn>
        </v-col>
    </v-row>
</template>
<script>
    export default {
        name: 'Button',
        data: () => ({
            buttonItems: ['x-small', 'small', 'default', 'large', 'x-large']
        }),
    }
</script>
<style>

</style>
