<template>
  <div>
    <h1>{{ state }}</h1>
    <Example />
  </div>
</template>

<script setup>
import {
  provide,
  inject,
  defineProps,
  defineEmits,
  ref,
  reactive,
  computed,
  watch,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";

// Components Import
import Example from "@/components/Example.vue";

// Directives
const vFocus = {
  mounted: (el) => el.focus(),
};

provide("exampleProvide", "exampleMSG");

const message = inject("exampleInject");

const props = defineProps(["exampleProp"]);

defineEmits(["event1", "event2"]);

// data() => equivalent to:
const state = ref(1); // Any type
const reactiveState = reactive({ value: 1 }); // Object types

const computedState = computed(() => {
  return state.value ? "ON" : "Off";
});

watch(state, (val) => {
  console.log(val);
});

// On beforeCreate & created script...

onBeforeMount(() => {
  console.log("beforeMount");
});

onMounted(() => {
  console.log("mount");
});

onBeforeUpdate(() => {
  console.log("beforeUpdate");
});

onUpdated(() => {
  console.log("update");
});

onBeforeUnmount(() => {
  console.log("beforeUnmount");
});

onUnmounted(() => {
  console.log("unmounted");
});

// methods: => equivalent to:
function increment() {
  state.value++;
}
</script>
