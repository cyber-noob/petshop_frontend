<template>
  <div class="q-pa-md example-row-equal-width">

    <div class="row wrap">
      <div class="q-pa-md items-start q-gutter-md" v-for="i in 5" :key="i">
        <q-card class="col my-card" flat bordered>
          <q-img src="https://cdn.quasar.dev/img/chicken-salad.jpg" />

          <q-card-section>
            <q-btn
              fab
              color="primary"
              icon="place"
              class="absolute"
              style="top: 0; right: 12px; transform: translateY(-50%);"
            />

            <div class="row no-wrap items-center">
              <div class="col text-h6 ellipsis">
                Cafe Basilico
              </div>
              <div class="col-auto text-grey text-caption q-pt-md row no-wrap items-center">
                <q-icon name="place" />
                250 ft
              </div>
            </div>

            <q-rating v-model="stars" :max="5" size="32px" />
          </q-card-section>

          <q-card-section class="q-pt-none">
            <div class="text-subtitle1">
              $・Italian, Cafe
            </div>
            <div class="text-caption text-grey">
              Small plates, salads & sandwiches in an intimate setting.
            </div>
          </q-card-section>

          <q-separator />

          <q-card-actions>
            <q-btn flat round icon="event" />
            <q-btn flat color="primary">
              Reserve
            </q-btn>
          </q-card-actions>
        </q-card>
      </div>
    </div>

  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    return {
      stars: ref(4),
    };
  },
  data() {
    return {
      items: [
        {
          id: 1,
        },
        {
          id: 2,
        },
        {
          id: 3,
        },
        {
          id: 4,
        },
      ],
    };
  },
};
</script>

<style lang="sass">
.my-card
  width: 100%
  max-width: 300px

.example-row-equal-width
  .row > div
    padding: 10px 15px
  .row + .row
    margin-top: 1rem
</style>
