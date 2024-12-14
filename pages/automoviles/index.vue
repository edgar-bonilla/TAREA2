<template>
  <div class="container py-5">
    <h3 class="text-warning text-center text-uppercase fw-bold mb-5">Automóviles Destacados</h3>

    <div class="row">
      <div v-for="car in automoviles" :key="car.id" class="col-12 col-md-4 mb-4">
        <div class="card h-100 border-warning shadow-sm">
          <NuxtLink :to="`/automoviles/${car.id}`" class="text-decoration-none text-dark">
            <div class="card-body d-flex flex-column">
              <h5 class="card-title text-warning">{{ car.nombre }}</h5>
              
              <p class="card-text"><strong>Diseñado por:</strong> {{ car?.diseñador?.nombre ?? 'Desconocido' }}</p>
            </div>
          </NuxtLink>
        </div>
      </div>
    </div>

    <p v-if="automoviles.length === 0" class="text-center text-muted">No se encontraron automóviles.</p>
  </div>
</template>

<script setup>
const data = await queryContent('automoviles').only('items').findOne()


const disenadoresData = await queryContent('disenadores').only('items').findOne()


const automoviles = data?.items.map(car => {
  const diseñador = disenadoresData?.items?.find(d => d.id === car.diseñadorId)
  return { ...car, diseñador }
}) ?? []
</script>

<style scoped>
.card-body {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.card-title {
  font-family: 'Helvetica Neue', sans-serif;
}

.card-text {
  font-family: 'Roboto', sans-serif;
  font-size: 1rem;
  color: #555;
}
</style>
