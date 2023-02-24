<template>
    <div class="text-center ma-2">
        <v-snackbar v-model="snackbar">
            <p align="center"> {{ text }}</p>
           <slot></slot>
        </v-snackbar>
    </div>

</template>

<script>
export default {
    name: 'modal',
    data() {
        return {
            snackbar: '',
            mainText: ''
        }
    },
    props: ['text'],
 
}
</script>