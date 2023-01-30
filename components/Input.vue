<template>
  <div class="mb-5">
    <label
      :for="text"
      class="block mb-3 uppercase text-2xl font-medium text-center"
      >{{ text }}</label
    >
    <input
      :type="type"
      class="bg-gray-50 border rounded text-center border-gray-300 px-8 py-5 w-full placeholder:uppercase placeholder:text-center file:mr-5 file:py-2 file:px-6 file:rounded-full file:border-0 file:text-sm file:font-medium file:bg-blue-50 file:text-blue-700 hover:file:cursor-pointer hover:file:bg-gray-50 hover:file:text-gray-700"
      :name="name"
      :value="type == 'file' ? null : value"
      @change="onChange"
      @input="onInput"
      :placeholder="placeholder"
      :required="required"
    />
  </div>
</template>

<script lang="ts">
export default {
  name: "Input",

  props: {
    text: {
      type: String,
      default: "Label",
    },
    type: {
      type: String,
      default: "text",
    },
    name: {
      type: String,
      default: "",
    },
    value: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
      default: "",
    },
    required: {
      type: Boolean,
      default: false,
    },
  },

  methods: {
    onInput(event) {
      this.$emit(
        "input",
        this.type == "file" ? event.target.files[0] : event.target.value
      );
    },
    onChange(event) {
      this.$emit(
        "change",
        this.type == "file" ? event.target.files[0] : event.target.value
      );
    },
  },
};
</script>
