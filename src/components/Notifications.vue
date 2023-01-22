<template>
    <div class="text-center ma-2">
        <v-snackbar v-model="snackbar">
            <p>Здравствуйте, {{this.partOfDay}}</p>
            <template v-slot:action="{ attrs }" style="z-index: 2000 !important">
                <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
                    Close
                </v-btn>
            </template>
        </v-snackbar>
    </div>
</template>

<style scoped>
.text-center{
    position: fixed;
    top: 0;
}
</style>
<script>
export default {
    name: 'notifications',
    props: {
        snackbar: false,
        text: String,
    },
    data() {
        return {
            snackbar: true,
            text: '',
            timeout: 2000,
        }
    },
    computed:{
        partOfDay(){
            let currentTime = new Date().getHours()
            if(currentTime > 6 && currentTime < 12)  this.text = 'Доброе утро'
            if(currentTime > 12 && currentTime < 18)  this.text = 'Добрый день'
            if(currentTime > 18 && currentTime < 0)  this.text = 'Добрый вечер'
            if(currentTime > 0 && currentTime < 6)  this.text = 'Доброй ночи'
        }
    }
}
</script>