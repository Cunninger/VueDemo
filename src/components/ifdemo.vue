<template>
    <div>
        <input type="text" v-model="tempValue" @keyup.enter="showContent" />
        <button @click="showContent">确认</button>
        <h1>{{ inputValue }}</h1>
  
    </div>
</template>

<script>
export default {
    data() {
        return {
            inputValue: '',
            tempValue: ''
        };
    },
    methods: {
        showContent() {
            this.inputValue = this.tempValue;
        }
    }
};
</script>