<template>
  <div class="flex" :class="containerClassesComputed">
    <button @click="onClick" :class="classes" :disabled="disabled" :type="type">
      <span v-if="heartIcon" class="absolute left-2">
        <HeartIcon />
      </span>
      <span v-if="!loading" class="uppercase" :class="spanClasses">
        {{ text }}</span
      >
      <CircleLoader :fillColor="'#FFFFFF'" :width="40" v-if="loading" />
    </button>
  </div>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: {
      type: String,
      default: null,
    },
    type: {
      type: String,
      default: "button",
      validator: function (value) {
        return ["button", "submit"].indexOf(value) !== -1;
      },
    },
    heartIcon: {
      type: Boolean,
      default: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    loading: {
      type: Boolean,
      default: false,
    },
    margin: {
      type: Boolean,
      default: true,
    },
    icon: {
      type: String,
      default: null,
    },
    additionalClasses: {
      type: Array,
      default: function () {
        return [];
      },
    },
    containerClasses: {
      type: Object,
      default: function () {
        return {};
      },
    },
    textClasses: {
      type: Array,
      default: function () {
        return [];
      },
    },
    height: {
      type: String,
      default: "h-4",
    },
    reversedIcon: {
      type: Boolean,
      default: false,
    },
    fullWidth: {
      type: Boolean,
      default: true,
    },
  },
  computed: {
    classes: function () {
      return [
        this.reversedIcon ? "flex-row-reverse" : "relative",
        ...this.additionalClasses,
      ];
    },
    spanClasses: function () {
      return [...this.textClasses];
    },
    containerClassesComputed: function () {
      let classesTemp = {
        "w-full": this.fullWidth,
        "mb-2": this.margin,
        ...this.containerClasses,
      };

      return classesTemp;
    },
  },
  methods: {
    onClick() {
      this.$emit("onClick");
    },
  },
};
</script>
