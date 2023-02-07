<template>
    <div class="text-center ma-2">
        <v-snackbar v-model="snackbar">
            <p>Здравствуйте, {{ partOfDay }}</p>
            <template v-slot:action="{ attrs }" style="z-index: 2000 !important">
                <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
                    Close
                </v-btn>
            </template>
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
    computed: {
        partOfDay: function() {
            let currentTime = new Date().getHours()
            console.log(typeof currentTime)
            if (currentTime > 6 && currentTime < 12) {
                console.log('1')
                return this.mainText = 'Доброе утро';
            }
            if (currentTime > 12 && currentTime < 18) {
                console.log('2')
                return this.mainText = 'Добрый день'
            }
            if (currentTime > 18 && currentTime < 0) {
                console.log('3')
                return this.mainText = 'Добрый вечер';
            }
            if (currentTime > 0 && currentTime < 6) {
                return this.mainText = 'Доброй ночи'
            } else {
                console.log('ОШИБКА')
            }

        }
    }

}
</script>