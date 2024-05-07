<template>

    <div class="background">

        <div>

            <!-- <div v-for="(message, index) in messages" :key="index"> -->
                <!-- <p>{{ message.role }}: <span v-for="(char, i) in message.content" :key="i">{{ char }}</span></p> -->
                <!-- <p class="message">{{ message.role }}: <span v-for="(char, i) in message.content" :key="i">{{ char }}</span></p>
            </div> -->

            <!-- <div v-for="(message, index) in messages" :key="index">
                   <p class="message" v-html="message.content"></p>
               </div> -->

               <div v-for="(message, index) in messages" :key="index">
                <p :class="{'user-message': message.role === 'user', 'bot-message': message.role === 'bot'}" v-html="message.content"></p>
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
            
            <!-- <button @click="document.body.style.backgroundImage = 'url(/aabc.jpg)'" style="position:fixed; bottom: 0cm; left: 30%; width: 50px; height:50px;">图片1</button> -->
        </div>

    </div>
</template>

<script>
   import axios from 'axios';
 // 使用命名导入而不是默认导入
import { marked } from 'marked';

   export default {
 
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
                   this.messages.push({ role: 'user', content: this.content });
                   this.messages.push({ role: 'bot', content: marked(response.data.choices[0].message.content) });
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
    background-image: url('/pic/aabc.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: repeat-y; /* 使背景图片在垂直方向上重复 */
    height: auto; /* 设置高度为auto，随内容增长 */
    min-height: 100vh; /* 最小高度为视口高度 */
    width: 100vw;
}


.user-message {
    width: 500px; /* 设置消息的最大宽度 */
    border: 2px solid blue; /* 用户消息的边框颜色 */
    padding: 10px;
    margin-bottom: 5px;
    background-color: #f4f4f4;
    border-radius: 10px;
}

.bot-message {
    width: 500px; /* 设置消息的最大宽度 */
    border: 2px solid green; /* 机器人消息的边框颜色 */
    padding: 10px;
    margin-bottom: 5px;
    background-color: #e0e0e0;
    border-radius: 10px;
}
.message {
    width: 500px; /* 设置消息的最大宽度 */
    word-wrap: break-word; /* 允许在单词内换行 */
    margin: 5px 0; /* 添加一些垂直间距 */
    padding: 10px; /* 增加内边距 */
    background-color: #f4f4f4; /* 背景色 */
    border-radius: 10px; /* 圆角边框 */
}
</style>