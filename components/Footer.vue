<template>
  <footer class="footer">
    <div class="footer-github">
      <a href="https://github.com/yeyuqiudeng/browser-default-value" target="_blank">
        <i class="iconfont icon-github"></i>
      </a>
    </div>
  </footer>
</template>
<style scoped>
    .footer {
      width: 100%;
      position: fixed;
      left: 0;
      bottom: 0;
      height: 120px;
      background: #324057;
      text-align: center;
    }
    .footer-github {
      height: 100%;
    }
    .footer a {
      line-height: 120px;
    }
    .footer .icon-github {
      width: 32px;
      height: 32px;
      font-size: 32px;
      color: #9d99ab;
      background-color: transparent;
      transition: .3s;
      display: inline-block;
    }
    .footer .icon-github:hover { 
      transform: scale(1.2);
      transform-origin: center center;      
      color: #fff;
    }    
</style>