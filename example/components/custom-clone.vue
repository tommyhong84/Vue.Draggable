<template>
  <div class=" justify-content-center jumbotron">
    <div class="row">
      <div class="col-3">
        <h3>Draggable 1</h3>
        <draggable
          class="dragArea list-group"
          :list="list1"
          :options="{ group: { name: 'people', pull: 'clone', put: false } }"
          :clone="cloneDog"
          @change="log"
        >
          <div
            class="list-group-item"
            v-for="element in list1"
            :key="element.id"
          >
            {{ element.name }}
          </div>
        </draggable>
      </div>

      <div class="col-3">
        <h3>Draggable 2</h3>
        <draggable
          class="dragArea list-group"
          :list="list2"
          :options="{ group: 'people' }"
          @change="log"
        >
          <div
            class="list-group-item"
            v-for="element in list2"
            :key="element.id"
          >
            {{ element.name }}
          </div>
        </draggable>
      </div>

      <rawDisplayer class="col-3" :value="list1" title="List 1" />

      <rawDisplayer class="col-3" :value="list2" title="List 2" />
    </div>
  </div>
</template>

<script>
import draggable from "@/vuedraggable";
import rawDisplayer from "./raw-displayer.vue";
let idGlobal = 8;
export default {
  name: "clone",
  components: {
    draggable,
    rawDisplayer
  },
  data() {
    return {
      list1: [
        { name: "dog 1", id: 1 },
        { name: "dog 2", id: 2 },
        { name: "dog 3", id: 3 },
        { name: "dog 4", id: 4 }
      ],
      list2: [
        { name: "cat 5", id: 5 },
        { name: "cat 6", id: 6 },
        { name: "cat 7", id: 7 }
      ]
    };
  },
  methods: {
    log: function(evt) {
      window.console.log(evt);
    },
    cloneDog({ id }) {
      return {
        id: idGlobal++,
        name: `cat ${id}`
      };
    }
  }
};
</script>
<style scoped></style>
