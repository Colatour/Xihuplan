<template>
    <div class="">
        <button @click='GO'>OK</button>
        {{ mean_value }}
    </div>
</template>

<script>
    export default {
        props: ['value'],
        data() {
            return {
                mean_value: {}
            }
        },
        computed: {
            Menus: function() {

            }
        },
        methods: {
            // local端先用Chrome抓取一個跨域小套件
            // https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi
            GO: function() {
                fetch(`http://opendata.epa.gov.tw/ws/Data/REWXQA/?%24orderby=SiteName&%24skip=0&%24top=1000&format=json`
                 //,{method: 'GET', mode: 'no-cors'}
                 ,{method: 'GET'}
                )
                .then(response => response.json())
                .then(json => this.mean_value = json)
            }
        }
    }
</script>