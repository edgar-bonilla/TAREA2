<template>
  <div class="container py-5">
    <h3 class="text-warning text-center text-uppercase fw-bold mb-5">Diseñadores Destacados</h3>

    <div v-if="designers && designers.length > 0" class="row">
      <div v-for="designer in designers" :key="designer.id" class="col-12 col-sm-6 col-md-4 mb-4">
        <div class="card h-100 border-warning shadow-sm">
          <NuxtLink :to="`/disenadores/${designer.id}`" class="text-decoration-none text-dark">
            <div class="card-body d-flex flex-column justify-content-center align-items-center">
              <h5 class="card-title text-warning text-center fw-bold">{{ designer.nombre }}</h5>
              <p class="card-text text-center">País: {{ designer.pais }}</p>
            </div>
          </NuxtLink>
        </div>
      </div>
    </div>

    <p v-else class="text-center text-muted">No se encontraron diseñadores.</p>
  </div>
</template>

<script setup>
const data = await queryContent('disenadores').only('items').findOne()
const designers = data?.items ?? []
</script>

<style scoped>

</style>
