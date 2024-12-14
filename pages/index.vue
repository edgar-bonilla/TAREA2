<template>
  <div class="home text-center py-5">
    <h1 class="display-4 mb-4 text-warning">Bienvenido al Catálogo de Automóviles</h1>
    <p class="lead mb-5 text-light">Explora los vehículos más exclusivos, los diseñadores y fabricantes que hacen realidad el lujo sobre ruedas.</p>

    <div class="row justify-content-center mt-5">
      <!-- Tarjeta de Automóviles -->
      <div class="col-12 col-md-4 mb-4">
        <div class="card h-100 border-warning shadow-lg rounded-3">
          <router-link to="/automoviles" class="text-decoration-none text-dark">
            <div class="card-body d-flex flex-column justify-content-center text-center">
              <h2 class="card-title text-warning text-uppercase fw-bold">Automóviles</h2>
              <p class="card-text">Descubre los automóviles más rápidos y exclusivos del mundo.</p>
            </div>
          </router-link>
        </div>
      </div>

      <!-- Tarjeta de Diseñadores -->
      <div class="col-12 col-md-4 mb-4">
        <div class="card h-100 border-warning shadow-lg rounded-3">
          <router-link to="/disenadores" class="text-decoration-none text-dark">
            <div class="card-body d-flex flex-column justify-content-center text-center">
              <h2 class="card-title text-warning text-uppercase fw-bold">Diseñadores</h2>
              <p class="card-text">Conoce a los creativos detrás de estos increíbles automóviles.</p>
            </div>
          </router-link>
        </div>
      </div>

      <!-- Tarjeta de Fabricantes -->
      <div class="col-12 col-md-4 mb-4">
        <div class="card h-100 border-warning shadow-lg rounded-3">
          <router-link to="/fabricantes" class="text-decoration-none text-dark">
            <div class="card-body d-flex flex-column justify-content-center text-center">
              <h2 class="card-title text-warning text-uppercase fw-bold">Fabricantes</h2>
              <p class="card-text">Explora las marcas que fabrican estos vehículos de lujo.</p>
            </div>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage'
};
</script>

<style scoped>
/* Fondo principal con degradado */
.home {
  background: linear-gradient(135deg, #1c1c1c, #4e4e4e);
  color: #fff;
}

/* Título principal */
h1 {
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  color: #f1c40f;
}

/* Texto secundario (parrafo principal) */
p.lead {
  font-size: 1.25rem;
  color: #ddd;
}

/* Estilo de la tarjeta */
.card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.7);
  background-color: rgba(0, 0, 0, 0.75);
}

.card-title {
  font-family: 'Montserrat', sans-serif;
}

.card-text {
  font-family: 'Roboto', sans-serif;
  color: #555;
}

.text-warning {
  color: #f1c40f !important;
}

.text-light {
  color: #eee !important;
}

@media (max-width: 768px) {
  h1 {
    font-size: 2.5rem;
  }

  .lead {
    font-size: 1rem;
  }
}
</style>
