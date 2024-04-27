<!-- <template>
    <div class="{{ msg }}">测试</div>
</template>

<script>
export default {
    data() {
        return {
            msg: "active "
        }
    }
}
</script> -->


<!-- <template>
    <div :id="duId" :class="msg">测试</div>
</template>

<script>
export default {
    data() {
        return {
            msg: "cc",
            duId: "myDiv"
        }
    }
}
</script>

<style>
.cc {
    color: red;
    background-color: yellow;
}
</style> -->



<template>
    <div>
        <div :id="duId" :class="msg">测试</div>
        <button @click="changeStyle">改变样式</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            msg: "cc",
            duId: "myDiv"
        }
    },
    methods: {
        changeStyle() {
            this.msg = this.msg === 'cc' ? 'dd' : 'cc';
        }
    }
}
</script>

<style>
.cc {
    color: red;
    background-color: yellow;
}

.dd {
    color: blue;
    background-color: green;
}
</style>