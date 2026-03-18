<template>
  <div class="start-screen">
    <div class="title-container">
      <img
        src="/assets/img/title_logo.png"
        class="title-image"
        alt="游戏标题"
        onerror="this.src = ''"
      />
    </div>

    <div class="intro-card">
      <div class="intro-title">
        <span>剧情介绍</span>
      </div>
      <div class="intro-text">
        今天是周末，你正准备睡个懒觉，<br /><br />
        突然手机狂震，家族群里消息像连珠炮一样弹出来——<br /><br />
        家族成员的认知和钱包正在遭受“数字病毒”的全面入侵！<br /><br />
        你必须在他们受骗前，逐一击破这些陷阱。
      </div>
    </div>

    <button class="start-btn" @click="handleStart">我准备好了！</button>
  </div>
</template>

<script setup>
import { useGameStore } from "@/store/useGameStore";

const store = useGameStore();

const handleStart = () => {
  store.playClickAudio();
  store.startGame();
};
</script>

<style scoped>
/* 继承游戏容器的背景色，覆盖全屏 */
.start-screen {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: var(--color-bg-container, #f7ede2);
  z-index: 9999; /* 确保它在最顶层，盖住游戏主界面 */
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40px 20px;
  box-sizing: border-box;
}

/* 标题图片容器 */
.title-container {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 20px;
  margin-bottom: 30px;
  min-height: 120px; /* 给图片预留高度，防止加载时抖动 */
}

.title-image {
  width: 80%; /* 图片宽度自适应，你可以根据你的 png 实际比例调整 */
  max-width: 300px;
  object-fit: contain;
}

/* 剧情介绍白卡 */
.intro-card {
  background: #ffffff;
  width: 100%;
  border-radius: 16px;
  padding: 30px 20px;
  box-shadow: 0 8px 24px rgba(90, 70, 52, 0.08); /* 配合游戏色调的暖色阴影 */
  margin-bottom: 40px;
  position: relative;
}

.intro-title {
  text-align: center;
  margin-bottom: 25px;
}

/* 标题文字和底部的绿色小横线 */
.intro-title span {
  font-size: 18px;
  font-weight: bold;
  color: var(--color-accent, #07c160);
  position: relative;
  padding-bottom: 8px;
}

.intro-title span::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 24px;
  height: 3px;
  background-color: var(--color-accent, #07c160);
  border-radius: 2px;
}

/* 剧情正文 */
.intro-text {
  font-size: 15px;
  color: var(--color-text-dark, #5a4634);
  line-height: 1.6;
  text-align: center;
}

/* 底部大按钮 */
.start-btn {
  background-color: var(--color-accent, #07c160);
  color: #ffffff;
  width: 80%;
  height: 50px;
  border: none;
  border-radius: 25px;
  font-size: 18px;
  font-weight: bold;
  letter-spacing: 1px;
  box-shadow: 0 6px 16px rgba(7, 193, 96, 0.3);
  cursor: pointer;
  transition:
    transform 0.1s,
    box-shadow 0.1s;
}

.start-btn:active {
  transform: scale(0.96);
  box-shadow: 0 2px 8px rgba(7, 193, 96, 0.2);
}
</style>
