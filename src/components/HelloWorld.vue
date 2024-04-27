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
</script>  -->


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


<!-- 
<template>
    <div>
        <div :id="duId" :class="msg" :title="heelojsp">测试</div>
        <button @click="changeStyle">改变样式</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            msg: "cc",
            duId: "myDiv",
            heelojsp: "这是一个div"
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
</style> -->


<!-- <template>
    <div>
        <div :id="duId" :class="msg" :title="heelojsp">鼠标悬停看提示</div>
        <button @click="changeTitle">改变提示</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            msg: "cc",
            duId: "myDiv",
            heelojsp: "初始提示"
        }
    },
    methods: {
        changeTitle() {
            this.heelojsp = this.heelojsp === '初始提示' ? '新的提示' : '初始提示';
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


<!-- <template>
<div :class="union.msg":id="union.duId" :title="union.heelojsp">测测测</div>
</template>

<script>
export default{
    data(){
        return{
            union:{
                msg: "cc",
                duId: "myDiv",
                heelojsp: "初始提示"
            }
        }
    }
}

</script> -->


<template>
    <button :disabled="isButtionDisabled">
        按钮
    </button>
</template>

<script>
export default {
    data() {
        return {
            isButtionDisabled: false
        }
    }
}
</script>
