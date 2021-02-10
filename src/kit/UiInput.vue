<template>
    <label class="ui-input">
        <span class="ui-input__label">{{ label }}</span>
        <input
            ref="ui-input"
            class="ui-input__input"
            :type="type"
            :value="modelValue"
            :maxlength="maxLength"
            :placeholder="placeholder"
            :required="isRequired"
            @input="handleInput"
        />
    </label>
</template>


<script>
export default {
    name: "UiInput",
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
        type: {
            type: String,
            default: "text",
            validator: (val) => {
                return (
                [
                    "url",
                    "text",
                    "password",
                    "email",
                    "search",
                    "number",
                    "tel",
                ].indexOf(val) !== -1
                );
            },
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

.ui-input {
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