<template>
  <q-page class="q-pa-sm">
    <q-select v-model="model" :options="options" label="Standard" />
    Theme value : {{ model }}
    <q-card class="my-card q-pa-sm bg-primary text-info" style="width: 750px"
      >Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quia eum
      dolorem maiores labore officiis, adipisci praesentium dolorum id officia?
      Vero ex sed consectetur quibusdam laudantium voluptatem aliquid eveniet
      possimus esse.
    </q-card>
    <div class="q-pa-md q-gutter-sm">
      <q-btn
        color="white"
        text-color="black"
        label="Standard"
        @click="$q.dark.toggle()"
      />
      <q-btn color="primary" label="Primary" />
      <q-btn color="secondary" label="Secondary" />
      <q-btn color="amber" glossy label="Amber" />
      <q-btn color="brown-5" label="Brown 5" />
      <q-btn color="deep-orange" glossy label="Deep Orange" />
      <q-btn color="purple" label="Purple" />
      <q-btn color="black" label="Black" />
    </div>
    <q-input
      v-model="text"
      type="text"
      outlined
      label-color="primary"
      label="primaray"
      color="primary"
    />
    <q-card class="my-card bg-primary" style="width: 500px">
      <img src="https://cdn.quasar.dev/img/mountains.jpg" />
      <q-card-section>
        <div class="text-h6 text-info">Our Changing Planet</div>
        <div class="text-subtitle2 text-info">by John Doe</div>
      </q-card-section>
      <q-card-section class="text-info">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit
      </q-card-section>
    </q-card>
    <q-list bordered>
      <q-item clickable v-ripple>
        <q-item-section avatar>
          <q-icon color="primary" name="bluetooth" />
        </q-item-section>
        <q-item-section>Icon as avatar</q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
import { ref } from "vue";
import { useQuasar } from "quasar";
export default {
  setup() {
    const $q = useQuasar();

    // get status
    console.log($q.dark.isActive); // true, false

    // get configured status
    console.log($q.dark.mode); // "auto", true, false

    // set status
    $q.dark.set("auto"); // or false or "auto"
    const model = ref(null);
    return {
      model,
      options: ["orange", "red", "dark", "blue", "green"],
    };
  },
  watch: {
    model: {
      handler: function (val) {
        console.log(val);
        document.documentElement.setAttribute("data-theme", val);
      },
      immediate: true,
    },
  },
};
</script>
