<template>
  <div class="row">
    <div class="col-2 bg-black" style="height: 95vh">
      <svg
        width="80"
        height="80"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
        class="mt-5"
      >
        <path
          fill="#3b82f6"
          d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10s10-4.48 10-10S17.52 2 12 2zm0 4c1.93 0 3.5 1.57 3.5 3.5S13.93 13 12 13s-3.5-1.57-3.5-3.5S10.07 6 12 6zm0 14c-2.03 0-4.43-.82-6.14-2.88a9.947 9.947 0 0 1 12.28 0C16.43 19.18 14.03 20 12 20z"
        />
      </svg>
      <p class="text-secondary">Bienvenid@</p>
      <p class="text-secondary">{{ nombre }} {{ apellido }}</p>
    </div>
    <div class="col-9 ms-5 ps-5 text-start">
      <h3 class="text-black my-5">Resumen de tu cuenta</h3>
      <h5 class="text-black">Le diste me gusta al juego {{ juego }}</h5>
      <div class="card" style="width: 32rem">
        <div class="card-body">
          <p>¿Deseas comprar coins para este juego?</p>
          <button @click="add5Coins" type="button" class="btn btn-warning">
            <svg
              width="20"
              height="20"
              viewBox="0 0 512 512"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill="#000000"
                d="M512 80c0 18-14.3 34.6-38.4 48c-29.1 16.1-72.5 27.5-122.3 30.9c-3.7-1.8-7.4-3.5-11.3-5c-39.4-16.5-91.8-25.9-148-25.9c-8.3 0-16.4.2-24.5.6l-1.1-.6C142.3 114.6 128 98 128 80c0-44.2 86-80 192-80s192 35.8 192 80zm-351.3 81.1c10.2-.7 20.7-1.1 31.3-1.1c62.2 0 117.4 12.3 152.5 31.4c24.8 13.5 39.5 30.3 39.5 48.6c0 4-.7 7.9-2.1 11.7c-4.6 13.2-17 25.3-35 35.5c-.1.1-.3.1-.4.2c-.3.2-.6.3-.9.5c-35 19.4-90.8 32-153.6 32c-59.6 0-112.9-11.3-148.2-29.1c-1.9-.9-3.7-1.9-5.5-2.9C14.3 274.6 0 258 0 240c0-34.8 53.4-64.5 128-75.4c10.5-1.5 21.4-2.7 32.7-3.5zM416 240c0-21.9-10.6-39.9-24.1-53.4c28.3-4.4 54.2-11.4 76.2-20.5c16.3-6.8 31.5-15.2 43.9-25.5V176c0 19.3-16.5 37.1-43.8 50.9c-14.6 7.4-32.4 13.7-52.4 18.5c.1-1.8.2-3.5.2-5.3zm-32 96c0 18-14.3 34.6-38.4 48c-1.8 1-3.6 1.9-5.5 2.9C304.9 404.7 251.6 416 192 416c-62.8 0-118.6-12.6-153.6-32C14.3 370.6 0 354 0 336v-35.4c12.5 10.3 27.6 18.7 43.9 25.5C83.4 342.6 135.8 352 192 352s108.6-9.4 148.1-25.9c7.8-3.2 15.3-6.9 22.4-10.9c6.1-3.4 11.8-7.2 17.2-11.2c1.5-1.1 2.9-2.3 4.3-3.4V336zm32 0v-57.9c19-4.2 36.5-9.5 52.1-16c16.3-6.8 31.5-15.2 43.9-25.5V272c0 10.5-5 21-14.9 30.9c-16.3 16.3-45 29.7-81.3 38.4c.1-1.7.2-3.5.2-5.3zM192 448c56.2 0 108.6-9.4 148.1-25.9c16.3-6.8 31.5-15.2 43.9-25.5V432c0 44.2-86 80-192 80S0 476.2 0 432v-35.4c12.5 10.3 27.6 18.7 43.9 25.5C83.4 438.6 135.8 448 192 448z"
              />
            </svg>
            Agregar coins
          </button>
          <hr />
          <h5>Cantidad de coins comprados</h5>
          <div
            class="progress"
            role="progressbar"
            aria-label="Success example"
            aria-valuenow="25"
            aria-valuemin="0"
            aria-valuemax="100"
          >
            <div class="progress-bar" :class="bg" :style="valorStyle">
              $ {{ amount }}
            </div>
          </div>
          <p>{{ message }}</p>
        </div>
      </div>

      <div class="d-flex flex-row mt-3">
        <div
          class="text-bg-warning p-3 mb-3 rounded-start"
          style="max-width: 18rem"
        >
          <div class="card-body">
            <h5 class="card-title">% de finalización de juego</h5>
            <hr />
            <p class="card-text">
              17%
              <svg
                width="20"
                height="20"
                viewBox="0 0 512 512"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  fill="#000000"
                  d="M135.539 453.9a7.979 7.979 0 0 1-11.51-8.362L144.6 312.2l-95.02-95.789a8 8 0 0 1 4.4-13.53l133.17-21.643L256 76.2V17.833l-18.763 28.624l-69.126 105.455L48.843 171.3a39.847 39.847 0 0 0-31.626 27.122A40.52 40.52 0 0 0 16 203.183v15.276a39.894 39.894 0 0 0 10.862 20.488l83.65 84.327L92.4 440.663a39.979 39.979 0 0 0 57.548 41.812L256 428.977v-35.841Z"
                />
              </svg>
            </p>
          </div>
        </div>
        <div class="text-bg-success p-3 mb-3" style="max-width: 18rem">
          <div class="card-body">
            <h5 class="card-title">Logros en el juego</h5>
            <hr />
            <p class="card-text">
              166
              <svg
                width="20"
                height="20"
                viewBox="0 0 512 512"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  fill="#ffffff"
                  d="M399.9 80V32H112v48H32v38c0 32 9.5 62.79 26.76 86.61c13.33 18.4 34.17 31.1 52.91 37.21c5.44 29.29 20.2 57.13 50.19 79.83c22 16.66 48.45 28.87 72.14 33.86V436h-74v44h192v-44h-74v-80.49c23.69-5 50.13-17.2 72.14-33.86c30-22.7 44.75-50.54 50.19-79.83c18.74-6.11 39.58-18.81 52.91-37.21C470.5 180.79 480 150 480 118V80ZM94.4 178.8c-10.68-14.68-17.17-34.4-18.24-54.8H112v67.37c-3.94-1.14-12.92-6.12-17.6-12.57Zm323.2 0c-4.6 6.61-11.6 12.58-17.6 12.58c0-22.4 0-46.29-.05-67.38h35.9c-1.08 20.4-7.85 39.9-18.25 54.8Z"
                />
              </svg>
            </p>
          </div>
        </div>
        <div class="text-bg-info p-3 mb-3 rounded-end" style="max-width: 18rem">
          <div class="card-body">
            <h5 class="card-title">Recompensas</h5>
            <hr />
            <p class="card-text">
              200
              <svg
                width="20"
                height="20"
                viewBox="0 0 16 16"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  fill="#000000"
                  d="M10 12.2c-.3 0-.5-.1-.8-.2L8 11.5l-1.2.5c-.2.1-.5.2-.8.2c-.2 0-.3 0-.5-.1L5 16l3-2l3 2l-.6-3.9c-.1.1-.3.1-.4.1zm2.9-6.3c-.1-.2-.1-.5 0-.7l.6-1.2c.2-.4 0-.9-.5-1.1l-1.3-.5c-.2-.1-.4-.3-.5-.5L10.7.6c-.1-.4-.4-.6-.7-.6c-.1 0-.3 0-.4.1L8.3.7H8c-.1 0-.2 0-.3-.1L6.4.1C6.3 0 6.1 0 6 0c-.3 0-.6.2-.8.5l-.5 1.4c0 .2-.2.4-.4.5l-1.4.5c-.4.1-.6.6-.4 1.1l.6 1.3c.1.2.1.5 0 .7l-.6 1.2c-.2.4 0 .9.5 1.1l1.3.5c.2.1.4.3.5.5l.5 1.3c.1.4.4.6.7.6c.1 0 .2 0 .3-.1l1.3-.6c.1 0 .2-.1.3-.1s.2 0 .3.1l1.3.6c.1.1.2.1.3.1c.3 0 .6-.2.8-.5l.5-1.3c.1-.2.3-.4.5-.5l1.3-.5c.4-.2.7-.7.5-1.1l-.5-1.4zM8 9.6c-2.2 0-4-1.8-4-4s1.8-4 4-4s4 1.8 4 4s-1.8 4-4 4z"
                />
                <path fill="#000000" d="M11 5.6a3 3 0 1 1-6 0a3 3 0 0 1 6 0z" />
              </svg>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      nombre: this.$route.query.nombre,
      apellido: this.$route.query.apellido,
      juego: this.$route.query.game,
      coins: 0,
      valorStyle: "",
      amount: "",
      bg: "",
      message: "",
    };
  },
  methods: {
    add5Coins() {
      if (this.coins === 50) {
        this.message = "Llegaste al máximo de tu crédito";
        return;
      }
      this.coins = this.coins + 5;
      this.updateValorStyle();
      this.updateAmount();
      this.updateBg();
    },
    updateValorStyle() {
      this.valorStyle = `width: ${this.coins}%`;
    },
    updateAmount() {
      this.amount = `${this.coins}%`;
    },
    updateBg() {
      if (this.coins <= 20) {
        this.bg = "bg-success";
      }
      if (this.coins > 20 && this.coins <= 30) {
        this.bg = "bg-warning";
      }
      if (this.coins > 30) {
        this.bg = "bg-danger";
      }
    },
  },
};
</script>
