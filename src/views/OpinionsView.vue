<template>
  <div>
    <h3 class="text-black mt-3">
      Escribe tu opinion para el juego: {{ $route.params.name }}
    </h3>
    <form class="container text-black text-start" @submit.prevent="onSubmit">
      <div class="row my-2">
        <label class="ps-0">Nombre:</label>
        <input type="text" v-model="nombre" placeholder="Nombre" />
      </div>
      <div class="row my-2">
        <label class="ps-0">Opinión</label>
        <textarea
          v-model="opinion"
          placeholder="Tu opinion debe ir aqui"
        ></textarea>
      </div>
      <button type="submit" class="btn btn-info col-1 ps-0 ms-0">
        {{ editIndex === null ? "Agregar" : "Editar" }}
      </button>
    </form>
    <h2 class="text-black mt-3">A continuación podrás ver tu opinión</h2>
    <div
      v-if="opinions.length === 0"
      class="container alert alert-danger d-flex align-items-center"
      role="alert"
    >
      <p>No existen opiniones que mostrar.</p>
    </div>
    <div v-else>
      <div v-for="(opinion, index) in opinions" :key="index">
        <div class="container p-0">
          <div class="accordion" id="accordionExample">
            <div class="accordion-item">
              <h2 class="accordion-header">
                <button
                  class="accordion-button"
                  type="button"
                  data-bs-toggle="collapse"
                  data-bs-target="#collapseOne"
                  aria-expanded="true"
                  aria-controls="collapseOne"
                >
                  Opinion creada por: {{ opinion.name }}
                </button>
              </h2>
              <div
                id="collapseOne"
                class="accordion-collapse collapse show"
                data-bs-parent="#accordionExample"
              >
                <div class="accordion-body">
                  <p class="text-start">
                    <span class="fw-bold">Opinion:</span> {{ opinion.opinion }}
                  </p>
                </div>
              </div>
              <div class="text-start">
                <button
                  @click="deleteOp(index)"
                  type="button"
                  class="btn btn-danger"
                >
                  Eliminar
                </button>
                <button
                  @click="editOp(index)"
                  type="button"
                  class="btn btn-warning ms-5"
                >
                  Editar
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "OpinionsView",
  data() {
    return {
      nombre: "",
      opinion: "",
      opinions: [],
      editIndex: null,
    };
  },
  methods: {
    onSubmit() {
      if (this.editIndex === null) {
        this.opinions.push({ nombre: this.nombre, opinion: this.opinion });
      } else {
        this.opinions[this.editIndex].nombre = this.nombre;
        this.opinions[this.editIndex].opinion = this.opinion;
        this.editIndex = null;
      }
      this.nombre = "";
      this.opinion = "";
    },
    deleteOp(index) {
      this.opinions.splice(index, 1);
    },
    editOp(index) {
      this.editIndex = index;
      this.nombre = this.opinions[index].nombre;
      this.opinion = this.opinions[index].opinion;
    },
  },
};
</script>
