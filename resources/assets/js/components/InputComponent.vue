<template>
    <el-form-item
        :label="label"
        label-position="right"
        :required="required"
        :error="errorMessage">
        <el-input
            :type="nativeInputType"
            :name="name"
            :label="label"
            :placeholder="placeholder"
            :disabled="disabled"
            v-model="fieldValue"
            @change.native="emitFieldValueChangeEvent">
        </el-input>
    </el-form-item>
</template>

<script>
    import { FormItem, Input } from 'element-ui';

    export default {
        name: 'input-component',
        components: {
            'el-form-item': FormItem,
            'el-input': Input
        },
        model: {
            prop: 'fieldValue',
            event: 'change'
        },
        props: {
            nativeInputType: {
                type: String,
                default: 'text'
            },
            name: String,
            label: String,
            placeholder: String,
            fieldValue: [String, Number],

            /**
             * Rules
             */
            // Add a little start next to the label.
            required: {
                type: Boolean,
                default: false
            },
            disabled: {
                type: Boolean,
                default: false
            },

            errorMessage: {
                type: String,
                default: null
            }
        },
        mounted() {
            //console.log('Input mounted.')
            //setInterval(() => { console.log('fieldValue', this.name, this.fieldValue); }, 3000);
        },
        methods: {
            emitFieldValueChangeEvent() {
                this.$emit('update:fieldValue', this.fieldValue);
            },
        }
    }
</script>
