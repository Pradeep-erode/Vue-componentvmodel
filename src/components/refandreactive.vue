<template>
    <h1>{{ hik }}</h1>
    <h1>Count={{ countnum }}</h1>
    <h1>FullName ={{ firstname }} {{ lastname }}</h1>
    <h1>Hi I am array with in ref {{refcount}}</h1>
</template>

<script>

import { inject, toRefs } from 'vue'

export default {
    name: 'ref-reactive',
    props: {
        hik: String
    },
    data() {
        return {
            samplename:'My name is data option in option API'
        }
    },
    setup() {

        const countnum = inject('count', 0)
        const names = inject('fullname', {
            firstname: 'parven',
            lastname: 'kumar'
        })
        const refcount = inject('refcounter', 0)

        return {
            countnum,
            ...toRefs(names),
            refcount
        }
    }
}
</script>

<style>
</style>