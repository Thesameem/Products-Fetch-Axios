<script setup>

    // props
    const props = defineProps({
        product: {
            type: Object,
            default: {}
        }
    });

    // emit
    const emit = defineEmits(['delete', 'edit']);

    // user first character for avatar
    const FirstChar = () => {
        return '';
    };
    

</script>

<template>
    <li>
        <div class="avatar">
            <img :src="product.images[0]" alt="">
        </div>
        <div class="content">
            <h4>{{product.title}}</h4>
            <p>{{ product.description }}</p>
        </div>
        <div class="delete">
            <img src="./../images/chat-list/delete.svg" alt="delete">
        </div>
        <div class="edit">
            <img src="./../images/chat-list/edit.svg" alt="edit">
        </div>
    </li>
</template>