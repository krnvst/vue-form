<template>
  <div class="ui-select" :tabindex="tabindex" @blur="open = false">
    <div class="selected" :class="{ open: open }" @click="open = !open">
      {{ selected }}
    </div>
    <div class="items" :class="{ 'select--hide': !open }">
      <div
        v-for="(option, i) of options"
        :key="i"
        @click="
          selected = option;
          open = false;
          $emit('input', option);
        "
      >
        {{ option }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UiSelect',
  props: {
    options: {
      type: Array,
      required: true,
    },
    default: {
      type: String,
      required: false,
      default: null,
    },
    tabindex: {
      type: Number,
      required: false,
      default: 0,
    },
  },
  data() {
    return {
      selected: this.default
        ? this.default
        : this.options.length > 0
        ? this.options[0]
        : null,
      open: false,
    };
  },
  mounted() {
    this.$emit("input", this.selected);
  },
};
</script>

<style lang="scss">
@import "@/styles/variables.scss";

.ui-select {
  position: relative;
  width: 100%;
  text-align: left;
  outline: none;
  height: 2rem;
  line-height: 30px;
  margin: 0 0 1rem;

	& .selected {
		background-color: $white;
		border: 1px solid $gray;
		color: $black;
		padding-left: $padding * 2;
		cursor: pointer;
		user-select: none;
	}

	& .selected.open {
		border: 1px solid $gray;
	}

	& .selected:after {
		position: absolute;
		content: "";
		top: 14px;
		right: 1em;
		width: 0;
		height: 0;
		border: 5px solid transparent;
		border-color: $gray transparent transparent transparent;
	}

	& .items {
		color: #000;
		overflow: hidden;
		border-left: 1px solid $gray;
		border-right: 1px solid $gray;
		border-bottom: 1px solid $gray;
		position: absolute;
		background-color: #fff;
		left: 0;
		right: 0;
		z-index: 1;
	}

	& .items div {
		color: $black;
		padding-left: 1em;
		cursor: pointer;
		user-select: none;
	}

	& .items div:hover {
		background-color: $gray-hover;
	}
}

.select--hide {
  display: none;
}
</style>
