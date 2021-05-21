<template>
  <input
    type="checkbox"
    class="field"
    :checked="modelValue"
    @change="$emit('update:modelValue', $event.target.checked)"
    :id="uuid"
  />
  <label v-if="label" :for="uuid">{{ label }}</label>
</template>

<script>
import UniqueID from "../utils/UniqueID";

export default {
  name: "BaseCheckbox",
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: Boolean,
      default: false,
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
