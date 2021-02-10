<template>
    <label class="ui-textarea">
        <span class="ui-textarea__label">{{ label }}</span>
        <textarea
            ref="ui-textarea"
            class="ui-textarea__input"
            :value="modelValue"
            :maxlength="maxLength"
            :placeholder="placeholder"
            :required="isRequired"
            @input="handleInput"
        >
        </textarea>
    </label>
</template>


<script>
export default {
    name: "UiTextarea",
    props: {
        modelValue: {
            type: [Number, String],
            default: "",
        },
        label: {
            type: String,
            default: "",
        },
        placeholder: {
            type: String,
            default: "",
        },
        maxLength: {
            type: Number,
            default: 500,
        },
        isRequired: {
            type: Boolean,
            default: false,
        }
    },
    methods: {
        handleInput(event) {
            this.$emit('update:modelValue', event.target.value)
        },
    },
};
</script>

<style lang="scss">
@import "@/styles/variables.scss";

.ui-textarea {
    display: flex;
    flex-direction: column;

    &__label {
        font-size: .9rem;
    }

    &__input {
        border: 1px solid $gray;
        padding: $padding;

        &:focus{
            outline: none;
        }
    }
}
</style>