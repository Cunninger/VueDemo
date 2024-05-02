<template>

    <div class="background">

        <div>

            <div v-for="(message, index) in messages" :key="index">
                <p>{{ message.role }}: <span v-for="(char, i) in message.content" :key="i">{{ char }}</span></p>
            </div>
            <select
                style="width: 100px; height: 25px;bottom: 0;left: 75%; position:fixed; bottom: 0; left: 65%; transform: translateX(-50%);"
                v-model="model">
                <option value="gpt-3.5">gpt-3.5</option>
                <option value="gpt-4">gpt-4</option>
            </select>
            <input v-model="content" @keyup.enter="sendRequest" placeholder="输入内容并按回车发送请求"
                style="position:fixed; bottom: 0; left: 50%; transform: translateX(-50%); width: 300px; height: 50px;">
            <input v-model="accessToken" placeholder="输入ghu"
                style=" position:fixed; bottom: 0.8cm; left: 61%; width: 100px; height:25px;">

            
            <button @click="messages = []" style="position:fixed; bottom: 0cm; left: 35%; width: 50px; height:50px;">清除</button>
        </div>

    </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            content: '',
            messages: [],
            model: 'gpt-3.5',  // 默认值
            accessToken: ''
        }
    },
    methods: {
        async sendRequest() {
            try {
                const response = await axios.post('https://proxy.cocopilot.org/v1/chat/completions', {
                    model: this.model,
                    messages: [
                        {
                            role: 'user',
                            content: this.content
                        }
                    ]
                }, {
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer ' + this.accessToken
                    }
                });

                this.messages.push({ role: 'user', content: this.content.split('') });
                this.messages.push({ role: 'bot', content: response.data.choices[0].message.content.split('') });
                this.content = '';
            } catch (error) {
                console.error(error);
            }
        }
    }
}
</script>

<style>
.background {
    background-image: url('/aabc.jpg');
    background-size: cover;
    /* 背景图片覆盖整个元素 */
    background-position: center;
    /* 背景图片居中 */
    height: 100vh;
    width: 100vw;
}



.message {
    width: 200px;
    /* 限制元素的宽度 */
    word-wrap: break-word;
    /* 允许在单词内换行 */
}
</style>