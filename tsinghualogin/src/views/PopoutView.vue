<template>
    <Popout uname="yangmh21"/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import Popout from '@/components/Popout.vue'; // @ is an alias to /src

@Options({
    components: {
        Popout,
    },
})
export default class PopoutView extends Vue {}
</script>