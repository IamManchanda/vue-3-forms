<template>
  <input
    type="radio"
    :checked="modelValue === value"
    :value="value"
    v-bind="$attrs"
    @change="$emit('update:modelValue', value)"
    :id="uuid"
  />
  <label v-if="label" :for="uuid">{{ label }}</label>
</template>

<script>
import UniqueID from "../utils/UniqueID";

export default {
  name: "BaseRadio",
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
    value: {
      type: [String, Number],
      required: true,
    },
  },
  setup() {
    const uuid = UniqueID().getID();
    return {
      uuid,
    };
  },
};
</script>
