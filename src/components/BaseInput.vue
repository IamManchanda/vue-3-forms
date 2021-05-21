<template>
  <label :for="uuid">{{ label }}</label>
  <input
    class="field"
    :placeholder="`Enter ${label}`"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    v-bind="$attrs"
    :id="uuid"
  />
</template>

<script>
import UniqueID from "../utils/UniqueID";

export default {
  name: "BaseInput",
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
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
