<template>
  <div class="container py-5">
    <h3 class="text-center mb-4 text-warning text-uppercase fw-bold">Detalles del Automóvil</h3>

    <div v-if="car" class="card mx-auto border-warning shadow-lg" style="max-width: 900px;">
      <div class="row g-0">
    
        <div class="col-md-6 d-flex align-items-center">
          <img :src="car?.imagen" alt="Imagen de {{ car?.nombre }}" class="img-fluid rounded-start" />
        </div>
        
     
        <div class="col-md-6">
          <div class="card-body">
         
            <h3 class="card-title text-warning text-center text-uppercase fw-bold">{{ car?.nombre }}</h3>

            <div class="info-section mt-4">
           
              <p class="mb-1">
                <strong class="text-warning">Fabricante: </strong> 
                <span>{{ car?.marca?.nombre }} ({{ car?.marca?.pais }})</span>
              </p>

            
              <p class="mb-1">
                <strong class="text-warning">Año: </strong> 
                <span> {{  car?.anio }}</span>
              </p>

           
              <p class="mb-1">
                <strong class="text-warning">Precio: </strong> 
                <span >{{ car?.precio }}</span>
              </p>

             
              <p class="mb-1">
                <strong class="text-warning">Descripción: </strong> 
                <span>{{ car?.descripcion }}</span>
              </p>

             
              <p class="mb-1">
                <strong class="text-warning">Diseñador: </strong> 
                <span >{{ car?.diseñador?.nombre }}</span>
              </p>

              <p class="mb-1">
                <strong class="text-warning">Caballaje: </strong> 
                <span>{{ car?.caballaje }} CV</span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div v-else class="text-center mt-5">
      <p class="text-muted">El automóvil no fue encontrado.</p>
    </div>
  </div>
</template>

<script setup>
const route = useRoute()
const carId = route.params.slug 


const automovilesData = await queryContent('automoviles').only('items').findOne()
const fabricantesData = await queryContent('fabricantes').only('items').findOne()
const disenadoresData = await queryContent('disenadores').only('items').findOne()

const car = automovilesData?.items?.find(c => c.id === parseInt(carId))

if (car) {
  const marca = fabricantesData?.items?.find(f => f.id === car.marcaId)
  const diseñador = disenadoresData?.items?.find(d => d.id === car.diseñadorId)

  car.marca = marca
  car.diseñador = diseñador
}
</script>

<style scoped>
.card {
  border-radius: 15px;
  border-top: 5px solid #e67e22;
}

.card-body {
  padding: 20px;
}

.card-title {
  font-size: 2rem;
  color: #e67e22;
}

.info-section p {
  font-size: 1rem;
  color: #555;
}

.info-section strong {
  font-weight: 600;
}

.img-fluid {
  border-radius: 15px 0 0 15px;
}

@media (max-width: 768px) {
  .img-fluid {
    border-radius: 15px 15px 0 0;
  }

  .card-body {
    padding: 15px;
  }

  .card-title {
    font-size: 1.8rem;
  }

  .info-section p {
    font-size: 0.95rem;
  }
}
</style>
