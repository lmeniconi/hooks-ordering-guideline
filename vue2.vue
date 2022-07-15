<template>
  <div>
    <h1>{{ state }}</h1>
    <Example />
  </div>
</template>

<script>
import Example from "@/components/Example.vue";

// Focus Directive
const focus = {
  mounted: (el) => el.focus(),
};

export default {
  components: {
    Example,
  },

  directives: {
    focus,
  },

  provide: {
    exampleProvide: "exampleMSG",
  },

  inject: ["exampleInject"],

  props: ["exampleProp"],

  emits: ["event1", "event2"],

  data() {
    return {
      state: 1,
    };
  },

  computed: {
    computedState() {
      return this.state ? "ON" : "Off";
    },
  },

  watch: {
    state(val) {
      console.log(val);
    },
  },

  beforeCreate() {
    console.log("beforeCreate");
  },

  created() {
    console.log("created");
  },

  beforeMount() {
    console.log("beforeMount");
  },

  mounted() {
    console.log("mount");
  },

  beforeUpdate() {
    console.log("beforeUpdate");
  },

  updated() {
    console.log("updated");
  },

  beforeUnmount() {
    console.log("beforeUnmount");
  },

  unmounted() {
    console.log("unmounted");
  },

  methods: {
    increment() {
      this.state++;
    },
  },
};
</script>
