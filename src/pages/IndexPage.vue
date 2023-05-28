<template>
  <div class="absolute-center full-width q-pa-xl">
    <q-form @submit="onSubmit" class="q-gutter-md">
      <q-select
        name="preferred_state"
        v-model="state"
        :options="options"
        color="primary"
        filled
        clearable
        label="Preferred State"
      />

      <q-select
        name="preferred_city"
        v-model="city"
        :options="options"
        color="primary"
        filled
        clearable
        label="Preferred City"
      />

      <q-select
        name="preferred_area"
        v-model="area"
        :options="options"
        color="primary"
        filled
        clearable
        label="Preferred Area"
      />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
      </div>
    </q-form>

    <q-card
      v-if="submitted"
      flat
      bordered
      class="q-mt-md"
      :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-2'"
    >
      <template v-if="submitEmpty">
        <q-card-section>
          Submitted form contains empty formData.
        </q-card-section>
      </template>
      <template v-else>
        <q-card-section>
          Submitted form contains the following formData (key = value):
        </q-card-section>
        <q-separator />
        <q-card-section class="row q-gutter-sm items-center">
          <div
            v-for="(item, index) in submitResult"
            :key="index"
            class="q-px-sm q-py-xs bg-grey-8 text-white rounded-borders text-center text-no-wrap"
          >{{ item.name }} = {{ item.value }}</div>
        </q-card-section>
      </template>
    </q-card>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const submitted = ref(false);
    const submitEmpty = ref(false);
    const submitResult = ref([]);

    return {
      state: ref(''),
      city: ref(''),
      area: ref(''),

      options: [
        {
          label: 'Rock',
          value: 'rock',
        },
        {
          label: 'Funk',
          value: 'funk',
        },
        {
          label: 'Pop',
          value: 'pop',
        },
      ],

      submitted,
      submitEmpty,
      submitResult,

      onSubmit(evt) {
        const formData = new FormData(evt.target);
        const data = [];

        formData.forEach((value, name) => data.push({ name, value }));

        submitted.value = true;
        submitResult.value = data;
        submitEmpty.value = data.length === 0;
      },
    };
  },
};
</script>
