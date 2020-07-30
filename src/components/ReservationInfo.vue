<template>
    <div class="display">
        <h3>{{info}}</h3>
    </div>
</template>

<script>
export default {
    name: "ReservationInfo",
    components:{
    },
    props: ["info"]
}
</script>

<style scoped>
    .display{
        border-bottom: 1px #1A3E7A solid;
    }
            
</style>