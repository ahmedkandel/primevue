<template>
	<JTPDropdown :modelValue="page" :options="pageOptions" optionLabel="label" optionValue="value"
        @update:modelValue="onChange($event)" class="p-paginator-page-options"></JTPDropdown>
</template>

<script>
import Dropdown from 'primevue/dropdown';

export default {
    name: 'JumpToPageDropdown',
    inheritAttrs: false,
    emits: ['page-change'],
    props: {
        page: Number,
        pageCount: Number
    },
    methods: {
        onChange(value) {
            this.$emit('page-change', value);
        }
    },
    computed: {
        pageOptions() {
            let opts = [];
            for(let i= 0; i < this.pageCount; i++) {
                opts.push({label: String(i), value: i})
            }
            return opts;
        }
    },
    components: {
        'JTPDropdown': Dropdown
    }
}
</script>
