<template>
  <div class="container py-5">
    <h3 class="text-center mb-4 text-warning text-uppercase fw-bold">Detalles del Diseñador</h3>

    <div v-if="designer" class="card mx-auto border-warning shadow-lg" style="max-width: 900px;">
      <div class="row g-0">
        <div class="col-md-6 d-flex align-items-center">
          <img :src="designer?.imagen" alt="Imagen de {{ designer?.nombre }}" class="img-fluid rounded-start" />
        </div>
        
        <div class="col-md-6">
          <div class="card-body">
            <h3 class="card-title text-warning text-center text-uppercase fw-bold">{{ designer?.nombre }}</h3>

            <div class="info-section mt-4">
              <p class="mb-1">
                <strong class="text-warning">País: </strong> 
                <span>{{ designer?.pais }}</span>
              </p>

              <p class="mb-1">
                <strong class="text-warning">Biografía: </strong> 
                <span>{{ designer?.biografia }}</span>
              </p>

              <p class="mb-1">
                <strong class="text-warning">Estilo: </strong> 
                <span>{{ designer?.estilo }}</span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div v-else class="text-center mt-5">
      <p class="text-muted">El diseñador no fue encontrado.</p>
    </div>

    <!-- Contenedor para los comentarios -->
    <div id="utteranc-comments" class="mt-5"></div>
  </div>
</template>

<script setup>
const route = useRoute()
const designerId = route.params.slug 

const disenadoresData = await queryContent('disenadores').only('items').findOne()

const designer = disenadoresData?.items?.find(d => d.id === parseInt(designerId))

onMounted(() => {
  // Agregamos el script de Utterances
  const script = document.createElement('script')
  script.src = 'https://utteranc.es/client.js'
  script.async = true
  script.setAttribute('repo', 'edgar-bonilla/TAREA2') // Reemplaza por tu repositorio
  script.setAttribute('issue-term', 'pathname')
  script.setAttribute('theme', 'github-light') // Tema claro
  script.setAttribute('crossorigin', 'anonymous')
  document.getElementById('utteranc-comments').appendChild(script)
})
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
