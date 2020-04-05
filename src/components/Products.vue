<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="card text-center my-5" style="width: 18rem;">
          <div class="card-header">{{ product.name }}</div>
          <div class="card-body">
            <div class="card-text text-muted">
              <p>${{ product.price }}</p>
            </div>
            <button :disabled="isInCart" @click="$emit('add-to-cart', product)" class="btn btn-primary form-control">
              {{ isInCart ? 'Added to cart' : 'Add to cart' }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>  
</template>

<script>
export default {
  props: ['product', 'isInCart']
}
</script>