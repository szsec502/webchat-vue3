<script setup>
import { ref } from 'vue';
import Layout from './layout/index.vue';

const messages = ref([
  { type: 'user', content: '你好，我想问一个问题' },
  { type: 'ai', content: '你好！我是AI助手，很高兴为你服务。请问有什么我可以帮助你的？' }
]);

const inputMessage = ref('');

const sendMessage = () => {
  if (inputMessage.value.trim()) {
    messages.value.push({ type: 'user', content: inputMessage.value });
    inputMessage.value = '';
  }
};
</script>
<template>
  <Layout>
    <div class="chat-container">
          <div class="chat-messages" ref="messageContainer">
            <div v-for="(msg, index) in messages" 
                 :key="index" 
                 :class="['message', msg.type]">
              <div class="message-content">
                {{ msg.content }}
              </div>
            </div>
          </div>
          
          <div class="chat-input-container">
            <el-input
              v-model="inputMessage"
              type="textarea"
              :rows="3"
              placeholder="输入消息..."
              resize="none"
              @keyup.enter.exact.prevent="sendMessage"
            />
            <el-button
              type="primary"
              :disabled="!inputMessage.trim()"
              @click="sendMessage"
            >
              发送
            </el-button>
          </div>
        </div>
  </Layout>
</template>

<style scoped>
.chat-container {
  height: 100%;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.chat-messages {
  flex: 1;
  overflow-y: auto;
  overflow-x: hidden;
  padding: 20px;
  background-color: #f5f7f9;
  margin-bottom: 0;
}

.message {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
}

.message.user {
  align-items: flex-end;
}

.message.ai {
  align-items: flex-start;
}

.message-content {
  max-width: 80%;
  padding: 12px 16px;
  border-radius: 12px;
  font-size: 14px;
  line-height: 1.5;
  word-wrap: break-word;
}

.user .message-content {
  background-color: #409EFF;
  color: white;
  border-radius: 12px 12px 0 12px;
}

.ai .message-content {
  background-color: white;
  color: #333;
  border-radius: 12px 12px 12px 0;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.1);
}

.chat-input-container {
  padding: 20px;
  background-color: white;
  border-top: 1px solid #e6e6e6;
  display: flex;
  gap: 10px;
}

.chat-input-container .el-input {
  flex: 1;
}

.chat-input-container .el-button {
  align-self: flex-end;
}

@media (max-width: 768px) {
  .el-aside {
    width: 60px !important;
  }
  
  .el-menu-item span {
    display: none;
  }
  
  .message-content {
    max-width: 90%;
  }
}
</style>
