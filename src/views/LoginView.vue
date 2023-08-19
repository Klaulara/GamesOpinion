<template>
  <div>
    <h1 class="text-black">Para ver la información ingresa tus datos</h1>
    <button @click="login" type="button" class="btn btn-success">Ingresar Datos</button>
  </div>
</template>

<script>
export default {
  name: "LoginView",
  data() {
    return {
        nombre: "",
        apellido: "",
    };
  },
  methods: {
    login () {
        this.nombre = prompt('Ingrese nombre')
        this.apellido = prompt('Ingreso apellido')
        if(this.nombre.length > 0 && this.apellido.length > 0){
          this.$router.push(`/admin?nombre=${this.nombre}&apellido=${this.apellido}&game=${this.$route.query.game}`)
        }
    }
  },
};
</script>
