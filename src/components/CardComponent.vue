<template>
<div class="text-center my-4 gy-2">
    <img :src="item.image" alt="item.name" />
    <h4>{{ item.name }}</h4>
    <div>{{item.origin }}</div>
    <div class="fw-bold">{{ item.space }}</div>
</div>
</template>

<script>
export default {
name: 'CardComponent',
props: { 
    item: Object
     }
}
</script>

<style lang="scss" scoped>
@import "@/style/vars.scss";


h4{
    text-transform: uppercase;

    &:after{
        content: '';
        display: block;
        width: 50px;
        height: 3px;
        margin: 1rem auto;
        background-color: currentColor;
        border-radius: 15px;
    }
}
img{
    border-radius: 50%;
    box-shadow: 0 0 6px 3px rgba(#000, 0.15);
    width: 100%;
}
</style>