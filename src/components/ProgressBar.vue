<template>
  <div>
    <svg role="progressbar" width="200" height="200" viewBox="0 0 100 100">
      <circle
        cx="50%"
        cy="50%"
        :r="radius"
        fill="none"
        stroke="#e6e6e6"
        stroke-width="10"
      ></circle>
      <circle
        cx="50%"
        cy="50%"
        :r="radius"
        fill="none"
        stroke-width="10"
        :stroke-dashoffset="offset"
        :stroke-dasharray="array"
        stroke-linecap="round"
        style="transform: rotate(-90deg); transform-origin: 50% 50%"
        stroke="#F23869"
      ></circle>
      <text
        x="50%"
        y="50%"
        fill="#000"
        text-anchor="middle"
        dy="5px"
        font-size="20px"
        font-weight="400"
      >
        {{ percent }}
      </text>
    </svg>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Number,
      default: 0.5,
    },
  },
  data() {
    return {
      radius: 40,
    };
  },
  computed: {
    offset() {
      return this.radius * Math.PI * 2;
    },
    array() {
      return this.offset * (1 - this.value);
    },
    percent() {
      return `${Math.round(this.value * 100)} %`;
    },
  },
};
</script>

<style lang="scss" scoped></style>
