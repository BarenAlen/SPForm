<template>
    <ul class="tag-list">
        <li v-for="tag in tags" v-bind:key="tag">
            <span class="tag">{{ tag }}</span>
        </li>
    </ul>
</template>

<script>
export default {
    name: 'TagList',
    props: {
        tags: Array
    }
}
</script>


<style scoped>
    .tag {
        display: inline-block;
        position: relative;
        padding: 4px 12px 4px 26px;
        vertical-align: middle;
        border-radius: 5px;
        background: #fff;
        background-image: radial-gradient(circle at 13px 16px, #fff 4px, #000 5px, transparent 6px);
        box-shadow: 0 0 1px 1px rgba(0,0,0,0.5);
        font-size: 1rem;
        white-space: nowrap;
    }

    .tag:empty {
        display: none;
    }

    .tag-list {
        list-style: none;
        padding: 0;
        margin: 0;
        font-size: 0;
    }

    .tag-list li {
        display: inline-block;
        vertical-align: middle;
        margin: 10px 10px 0 0;
    }
</style>

