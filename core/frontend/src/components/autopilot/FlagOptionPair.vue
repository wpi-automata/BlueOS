<template>
    <div class="mb-5">
        <input type="text" v-model="flag" placeholder="Flag" style="border:3px solid black; margin-right: 5px"/>
        <input type="text" v-model="value" placeholder="Flag Value" style="border:3px solid black"/>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'FlagOptionPair',
    data() {
        return {
            flag: '',
            value: '',
        }
    },
    methods: {
        getData() : {data: {flag: string, value: string}} {
            return {
                    flag: this.flag,
                    value: this.value,
            }
        },
    },
})
</script>
