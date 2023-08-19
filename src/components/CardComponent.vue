<template>
  <div>
    <div class="card text-start" style="width: 18rem">
      <img :src="image" class="card-img-top" alt="image" />
      <div class="card-body">
        <h5 class="card-title">{{ title }}</h5>
      </div>
      <ul class="list-group list-group-flush">
        <li class="list-group-item">Rating: {{ rating }}</li>
        <li class="list-group-item">Released: {{ released }}</li>
        <li class="list-group-item">Updated: {{ update }}</li>
      </ul>
      <div class="card-body">
        <button @click="redirect" type="button" class="btn btn-primary">Opinar</button>
        <button @click="redirectTo" class="btn"> 
          <svg
            width="30"
            height="30"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill="#e00606"
              d="m12 21.35l-1.45-1.32C5.4 15.36 2 12.27 2 8.5C2 5.41 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.08C13.09 3.81 14.76 3 16.5 3C19.58 3 22 5.41 22 8.5c0 3.77-3.4 6.86-8.55 11.53L12 21.35Z"
            />
          </svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardComponent",
  props: {
    title: {
      type: String,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
    rating: {
      type: Number,
      required: true,
    },
    released: {
      type: String,
      required: true,
    },
    update: {
      type: String,
      required: true,
    },
  },
  methods: {
    redirect() {
      this.$router.push(`/opiniones/${this.title}`);
    },
    redirectTo() {
      this.$router.push(`/login?game=${this.title}`)
    }
  },
};
</script>
