<template>
    <div class="input-group">
        <input @keypress.prevent.enter="updateInput()" ref="input" type="text" class="form-control" :id="id" :name="name">
        <div class="input-group-append">
            <button @click="updateInput()" class="input-group-text icon-plus" type="button">+</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'InputList',
    props: ['id', 'name'],
    data() {
        return {
            itemsList: []
        }
    },
    methods: {
        updateInput() {
            let input = this.$refs.input;

            this.itemsList = this.itemsList.concat(input.value.split(/,|;/));
            this.$emit('input', this.itemsList);
            input.value = "";
            input.focus();
        }
    }
}
</script>
