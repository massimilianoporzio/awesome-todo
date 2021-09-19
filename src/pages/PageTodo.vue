<template>
  <q-page class="q-pa-md">
    <q-list bordered>
      <q-item v-ripple v-for="task in tasks" :key="task.id"
              clickable
              @click="task.completed = !task.completed">
        <q-item-section side top>
          <q-checkbox v-model="task.completed" />
        </q-item-section>

        <q-item-section>
          <q-item-label>{{task.name}}</q-item-label>
        </q-item-section>
      </q-item>




    </q-list>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "PageIndex",
  data() {
    return {
      tasks: [
        {
        id: 1,
        name: 'Go to shop',
        completed: false
        },
        {
          id: 2,
          name: 'Get bananas',
          completed: true
        },
        {
          id: 3,
          name: 'Get apples',
          completed: false
        }
      ],
    };
  },
});
</script>
