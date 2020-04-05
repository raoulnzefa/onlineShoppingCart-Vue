<template>
    <ul class="list-group">
        <h2>Cart:</h2>
        <li class="list-group-item" v-for="item in items" :key="item.id">
            {{ item.name }} : ${{ item.price }}
            <button @click="$emit('remove-from-cart', item)" class="btn badge badge-danger float-right">Remove</button>
        </li>
        <div class="card p-3 my-5">
            <h4 class="text-center">Total: ${{ total }}</h4>
        </div>
        <button :disabled="items.length === 0" @click="$emit('pay')" class="btn btn-info form-control">Pay Now</button>
    </ul>
</template>

<script>
export default {
    props: ['items'],
    computed: {
        total() {
            return this.items.reduce((acc, item) => acc + Number(item.price), 0)
        },
    },
}
</script>

<style scoped>
ul{
    text-align: left;
}
.card{
    border-radius: 15px;
    background-color: antiquewhite;
}
</style>