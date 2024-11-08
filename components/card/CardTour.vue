<template lang="pug">
div(class="card-container")
  div(class="card" v-for="tour in tours" :key="tour.id")
    div(class="card__header")
      div(class="card__picture")
        div(class="card__picture-overlay") &nbsp;
        img(src="@/assets/img/tours/tour-1-cover.jpg" alt="Tour 1" class="card__picture-img")
      h3(class="heading-tertirary")
        span {{ tour.name }}
    div(class="card__details")
      h4(class="card__sub-heading") {{ tour.difficulty }} {{ tour.duration }}-day tour
      p(class="card__text") {{ tour.summary }}
      div(class="card__data")
        svg(class="card__icon")
          use(xlink:href="@/assets/img/icons.svg#icon-map-pin")
        span {{ tour.location }}
      div(class="card__data")
        svg(class="card__icon") 
          use(xlink:href="@/assets/img/icons.svg#icon-calendar")
        span {{ tour.date }}
      div(class="card__data")
        svg(class="card__icon")
          use(xlink:href="@/assets/img/icons.svg#icon-flag")
        span {{ tour.stops }} stops
      div(class="card__data")
        svg(class="card__icon")
          use(xlink:href="img/icons.svg#icon-user")
        span {{ tour.maxGroupSize }} people
    div(class="card__footer")
      p
        span(class="card__footer-value") ${{ tour.price }}
        span(class="card__footer-text") per person
      p(class="card__ratings") 
        span(class="card__footer-value") {{ tour.rating }}
        span(class="card__footer-text") rating ({{ tour.ratingCount }})
      NuxtLink(:to="`/tours/${tour.id}`" class="btn btn--green btn--small") Details
  </template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    const search = ref("");
    const page = ref(1);

    // Mock data array for tours
    const tours = ref([
      {
        id: 1,
        name: "Discover Banff",
        difficulty: "easy",
        duration: 3,
        summary: "Explore the stunning landscapes of Banff.",
        location: "Banff, Canada",
        date: "April 2021",
        stops: 3,
        maxGroupSize: 25,
        price: 297,
        rating: 4.9,
        ratingCount: 21,
      },
      {
        id: 2,
        name: "Mountain Adventure",
        difficulty: "moderate",
        duration: 5,
        summary: "Experience the thrill of the Rockies.",
        location: "Jasper, Canada",
        date: "May 2021",
        stops: 4,
        maxGroupSize: 20,
        price: 399,
        rating: 4.7,
        ratingCount: 15,
      },
      {
        id: 3,
        name: "Safari Expedition",
        difficulty: "hard",
        duration: 7,
        summary: "Journey through the African wilderness.",
        location: "Serengeti, Tanzania",
        date: "June 2021",
        stops: 5,
        maxGroupSize: 12,
        price: 699,
        rating: 4.8,
        ratingCount: 34,
      },
      {
        id: 4,
        name: "Island Paradise",
        difficulty: "easy",
        duration: 4,
        summary: "Relax on the tropical beaches of Bali.",
        location: "Bali, Indonesia",
        date: "July 2021",
        stops: 2,
        maxGroupSize: 30,
        price: 499,
        rating: 4.6,
        ratingCount: 20,
      },
      {
        id: 5,
        name: "Desert Adventure",
        difficulty: "hard",
        duration: 6,
        summary: "Conquer the sand dunes of the Sahara.",
        location: "Sahara, Morocco",
        date: "August 2021",
        stops: 4,
        maxGroupSize: 15,
        price: 599,
        rating: 4.5,
        ratingCount: 28,
      },
      {
        id: 6,
        name: "Alaskan Wilderness",
        difficulty: "moderate",
        duration: 10,
        summary: "Explore the rugged terrains of Alaska.",
        location: "Anchorage, Alaska",
        date: "September 2021",
        stops: 6,
        maxGroupSize: 18,
        price: 899,
        rating: 4.9,
        ratingCount: 40,
      },
    ]);

    return {
      search,
      page,
      tours,
    };
  },
});
</script>
<!-- <script lang="ts">
// interface iIour {
//   name: string;
//   description: string;
// }
export default defineComponent({
  async setup() {
    const search = ref("");
    const page = ref(1);
    const { data: tours, error }: any = await useAsyncData(
      "tours",
      () =>
        $fetch(`/api/tour`, {
          method: "GET",
          baseURL: "http://localhost:8001",
          params: {
            page: page.value,
            search: search.value,
          },
        }),
      {
        watch: [page, search],
      }
    );
    return {
      search,
      page,
      tours,
    };
  },
});
</script> -->

<style lang="scss" scoped></style>
