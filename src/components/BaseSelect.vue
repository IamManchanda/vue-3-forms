<template>
  <label v-if="label" :for="uuid">{{ label }}</label>
  <select
    class="field"
    :value="modelValue"
    v-bind="{
      ...$attrs,
      onChange: ($event) => {
        $emit('update:modelValue', $event.target.value);
      },
    }"
    :id="uuid"
  >
    <option v-if="label" value="" disabled>Please {{ label }}</option>
    <option
      v-for="option in options"
      :value="option"
      :key="option"
      :selected="option === modelValue"
    >
      {{ option }}
    </option>
  </select>
</template>

<script>
import UniqueID from "../utils/UniqueID";

export default {
  name: "BaseSelect",
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
    options: {
      type: Array,
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
