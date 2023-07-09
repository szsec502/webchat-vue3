<script>
</script>
<template>

  <el-container style="height: 100vh;">

    <el-header>
      <el-row>
        <el-col :span="24">
          <div class="logo">  
            Logo
          </div>
        </el-col>
      </el-row>
    </el-header>

    <el-container>
    
      <el-aside width="200px">
      
        <el-menu
          style="height: 100%; background-color: #f5f5f5; overflow-y: auto;" 
          class="sidebar-menu"
        >
        
          <el-menu-item index="1">聊天记录1</el-menu-item>
        
          <el-menu-item index="2">聊天记录2</el-menu-item>
        
        </el-menu>
      
      </el-aside>
      
      <el-main>
      
        <div class="chat-main" style="display: flex; flex-direction: column;">
        
          <div 
            class="chat-history"
            style="flex: 1; overflow-y: auto;"  
          >
          
            <div class="message">
              消息1
            </div>
          
            <div class="message">
              消息2  
            </div>
            
          </div>
          
          <div class="chat-footer">
          
            <el-input
              type="textarea"
              autosize
              placeholder="请输入内容"
              class="chat-input"
            />
            
            <el-button
              type="primary"
              class="send-button"  
            >
              发送
            </el-button>
            
          </div>
          
        </div>
        
      </el-main>

    </el-container>

  </el-container>

</template>

<style>

  .sidebar-menu {
    height: 100%;
    overflow-y: auto;
  }

  .chat-main {
    height: 100%;
  }

  .chat-history {
    overflow-y: auto;
  }

  .chat-footer {
    position: absolute;
    bottom: 0;
    width: 100%;
  }

  .chat-input {
    width: calc(100% - 100px);
    display: inline-block;
  }

  .send-button {
    display: inline-block;
    width: 100px;
  }

</style>
