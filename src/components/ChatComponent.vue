<template>
  <div class="chat-container">
    <!-- White rounded box background -->
    <div class="white-box">
      <!-- Header -->
      <div class="header">
        <div class="left">
          <el-dropdown>
            <span class="el-dropdown-link">
              模型选择
              <el-icon class="el-icon--right">
                <arrow-down />
              </el-icon>
            </span>
            <template #dropdown>
              <el-dropdown-menu>
                <el-dropdown-item>Model 1</el-dropdown-item>
                <el-dropdown-item>Model 2</el-dropdown-item>
                <el-dropdown-item>Model 3</el-dropdown-item>
              </el-dropdown-menu>
            </template>
          </el-dropdown>
        </div>

        <div class="right">
          <el-button class="custom-button" circle>
            <el-icon><Share /></el-icon>
          </el-button>
        </div>
      </div>

      <!-- Chat window for displaying messages -->
      <div class="chat-window">
        <div v-for="(message, index) in messages" :key="index" :class="message.role">
          <div class="message">{{ message.text }}</div>
        </div>
      </div>

      <!-- Input box with upload and send icons -->
      <div class="input-box">
        <div class="icon-group">
          <el-button class="icon-button" circle>
            <el-icon><UploadFilled /></el-icon>
          </el-button>
        </div>

<!--        <div class="user_input">-->
<!--          <el-input-->
<!--          v-model="userMessage"-->
<!--          style="width: 400px"-->
<!--          :autosize="{ minRows: 1, maxRows: 2 }"-->
<!--          type="textarea"-->
<!--          @keyup.enter="sendMessage"-->
<!--          placeholder="给“ChatGPT”发送消息"-->
<!--          class="custom-input"-->
<!--        />-->
<!--        </div>-->

        <div class="send_message">
          <el-button @click="sendMessage" class="send-button" circle>
          <el-icon><Promotion /></el-icon>
        </el-button>

        </div>


      </div>
    </div>
  </div>
</template>

<script>
import { ArrowDown, Share, UploadFilled, Promotion } from '@element-plus/icons-vue'
import { ref } from 'vue';

export default {
  name: "ChatComponent",
  components: {
    ArrowDown,
    Share,
    UploadFilled,
    Promotion,
  },
  setup() {
    const messages = ref([
      { role: "user", text: "Hello, AI!" },
      { role: "ai", text: "Hello! How can I assist you today?" },
    ]);
    const userMessage = ref("");

    const sendMessage = () => {
      if (userMessage.value.trim() !== "") {
        messages.value.push({ role: "user", text: userMessage.value });
        userMessage.value = "";

        // Simulate AI response (replace this with actual API call if needed)
        setTimeout(() => {
          messages.value.push({ role: "ai", text: "This is a simulated response." });
        }, 1000);
      }
    };

    return {
      messages,
      userMessage,
      sendMessage,
    };
  },
};
</script>

<style scoped>
.chat-container {
  height: 100%;
}

.el-dropdown-link {
  color: black;
  font-weight: bold;
  font-size: 15px;
  display: flex;
  align-items: center;
  cursor: pointer;
}

.white-box {
  background-color: white;
  border-radius: 15px;
  padding: 10px;
  height: 98%;
  margin-top: 10px;
  margin-bottom: 10px;
  box-sizing: border-box;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

/* Header */
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 10%;
}

.custom-button {
  background-color: white;
  color: black;
  border: 1px solid #e0e0e0;
  font-size: 20px;
  margin: 0;
  padding-top: 0;
  padding-bottom: 0;
}

.custom-button:hover {
  background-color: #c0c0c0;
  color: black;
  border: 1px solid #c0c0c0;
}

/* Chat window */
.chat-window {
  flex-grow: 1;
  overflow-y: auto;
  margin: 10px 0;
}

.user {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 8px;
}

.ai {
  display: flex;
  justify-content: flex-start;
  margin-bottom: 8px;
}

.message {
  max-width: 60%;
  padding: 10px;
  border-radius: 8px;
  word-wrap: break-word;
}

.user .message {
  background-color: #ccc;
  color: black;
}

.ai .message {
  background-color: transparent;
  color: black;
}

/* Input box */
.input-box {
  display: flex;
  align-items: center;
  justify-content: space-between; /* 将元素分布在容器的两侧 */
  background-color: #f5f5f5; /* Light gray background */
  padding: 10px;
  border-radius: 20px;
  margin-top: 10px;
}

.custom-input ::v-deep .el-input__inner {
  background-color: black !important; /* Change background color */
  color: white !important; /* Change text color */
  border-color: gray !important; /* Optional border color */
  opacity: 1 !important; /* Ensures disabled state doesn’t reduce opacity */
}

/* Customize the placeholder color */
.custom-input ::v-deep .el-input__inner::placeholder {
  color: lightgray !important; /* Placeholder color */
}

.icon-group {
  display: flex;
  gap: 5px;
  margin-right: 10px;
}

.icon-button {
  background-color: transparent;
  color: black;
  border: none;
}

.icon-button:hover {
  background-color: #e0e0e0;
}

/*.input-field {*/
/*  flex: 1;*/
/*  border: none;*/
/*  background-color: black; !* Set the input field background to black *!*/
/*  color: white; !* Set text color to white for contrast *!*/
/*  outline: none;*/
/*  padding: 0;*/
/*}*/

.send-button {
  background-color: transparent;
  color: black;
  border: none;

}

.send-button:hover {
  background-color: #ccc;
}

</style>