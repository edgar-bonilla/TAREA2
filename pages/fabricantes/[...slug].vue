<template>
  <div class="container py-5">
    <h3 class="text-warning text-center text-uppercase fw-bold mb-5">{{ manufacturer?.nombre }}</h3>

    <div v-if="manufacturer" class="row justify-content-center">
      <div class="col-12 col-md-8">
        <div class="card border-warning shadow-sm">
          <div class="card-body">
            <h5 class="card-title text-center text-warning fw-bold">{{ manufacturer.nombre }}</h5>

            <ul class="list-group list-group-flush">
              <li class="list-group-item"><strong>Nombre:</strong> {{ manufacturer.nombre }}</li>
              <li class="list-group-item"><strong>Año de Fundación:</strong> {{ manufacturer.añoFundacion }}</li>
              <li class="list-group-item"><strong>País:</strong> {{ manufacturer.pais }}</li>
              <li class="list-group-item"><strong>Fundador:</strong> {{ manufacturer.fundador ? manufacturer.fundador : 'No disponible' }}</li>
              <li class="list-group-item"><strong>Información:</strong> {{ manufacturer.informacion }}</li>
            </ul>

          </div>
        </div>
      </div>
    </div>

    <p v-else class="text-center text-muted">El fabricante no fue encontrado.</p>
  </div>
</template>

<script setup>
const route = useRoute()
const manufacturerId = route.params.slug

let manufacturer = null
try {
  const data = await queryContent('fabricantes').only('items').findOne()
  manufacturer = data?.items?.find(f => f.id === parseInt(manufacturerId))

  if (!manufacturer) {
    console.warn('Fabricante no encontrado.')
  }
} catch (error) {
  console.error('Error al obtener los datos del fabricante:', error)
  manufacturer = null
}
</script>

<style scoped>

</style>
