# 🌟 CherryStudio 自定义主题
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/73d4e7f666f14f82863fee3b7d2ae5a6.png)![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c9b6f2e111b046f7b45f35eaa00c2229.png)
```
* *==============================================================================
 * 主题名称：CherryStudio - 霓虹黑紫 x BlurBerry毛玻璃融合版 (终极动态特效版)
 * 融合说明：保留原本地背景与黑紫霓虹输入框，全局应用高斯模糊玻璃拟物UI
 * 新增特效：AI能量流转边框、光纤滚动条、用户镭射气泡、代码块、全局文本选中高亮
 * 修复更新：修复浅色模式下渐变未到达左侧的问题，增加深色模式紫色文本选中色
 * * ==============================================================================*/

@import url("https://fontsapi.zeoseven.com/479/main/result.css");
@import url("https://fontsapi.zeoseven.com/3/main/result.css");
@import url("https://cdn.bootcdn.net/ajax/libs/github-markdown-css/5.8.1/github-markdown-dark.css");

/* ==========================================
   全局关键帧动画库
   ========================================== */
/* 输入框霓虹呼吸 */
@keyframes gradientFlow {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
@keyframes blinking {
  0% { filter: drop-shadow(rgba(94, 0, 153, 0.8) 0px 0px 4px); }
  25% { filter: drop-shadow(rgba(184, 41, 255, 0.9) 0px 0px 8px); }
  50% { filter: drop-shadow(rgba(184, 41, 255, 1) 0px 0px 15px); }
  75% { filter: drop-shadow(rgba(184, 41, 255, 0.9) 0px 0px 8px); }
  100% { filter: drop-shadow(rgba(94, 0, 153, 0.8) 0px 0px 4px); }
}

/* 特效1：AI气泡能量流转扫描 */
@keyframes aiEnergyFlow {
  0% { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}

/* 特效4：用户气泡全息镭射扫光 */
@keyframes holoFoil {
  0% { left: -100%; opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { left: 200%; opacity: 0; }
}

/* 特效5：代码块按钮赛博故障抖动 */
@keyframes glitch {
  0% { transform: translate(0) }
  20% { transform: translate(-2px, 1px) }
  40% { transform: translate(-1px, -1px) }
  60% { transform: translate(2px, 1px) }
  80% { transform: translate(1px, -1px) }
  100% { transform: translate(0) }
}

/* --- 根变量 (融合 BlurBerry 的模糊参数与基础设定) --- */
:root {
  --danger-color: rgba(255, 77, 110, 1);
  --danger-color-soft: rgba(255, 77, 110, .2);
  --danger-color-hard: rgba(255, 77, 110, .4);
  --navbar-background: unset;
  --box-shadow: 0 2px 8px rgba(33, 33, 33, 0.1);
  --blur: blur(40px); /* 核心高斯模糊参数 */
  --color-primary: #00C957; 
}

/* --- 全局背景基础样式 --- */
body {
  font-family: "TsangerYuMo W03", sans-serif;
  font-weight: normal;
  background-size: cover;
  background-position: center center;
  background-attachment: fixed;
  transition: background-image 0.3s linear, background-color 0.3s linear;
}

/* 核心容器透明以显示背景 */
#root > div,
body > div, 
#content-container {
  background: transparent !important;
}

/* ==========================================
   新增特效：全局文本选中高亮 (Matrix Selection)
   ========================================== */
/* 浅色模式：赛博绿选中色 */
[theme-mode="light"] ::selection {
  background: rgba(0, 201, 87, 0.3);
  color: #000;
  text-shadow: 0 0 2px rgba(0, 201, 87, 0.5);
}
/* 深色模式：霓虹紫选中色 */
[theme-mode="dark"] ::selection {
  background: rgba(184, 41, 255, 0.4);
  color: #fff;
  text-shadow: 0 0 5px rgba(184, 41, 255, 0.8);
}

/* ==========================================
   特效3：光纤滚动条 (全局隐形，悬浮点亮)
   ========================================== */
::-webkit-scrollbar {
  width: 6px;
  height: 6px;
  background: transparent;
}
::-webkit-scrollbar-track {
  background: transparent;
}
::-webkit-scrollbar-thumb {
  background: rgba(150, 150, 150, 0.2);
  border-radius: 10px;
  transition: background 0.3s ease;
}
body[theme-mode="dark"] ::-webkit-scrollbar-thumb:hover {
  background: #b829ff; /* 暗色模式霓虹紫 */
  box-shadow: 0 0 10px #b829ff;
}
body[theme-mode="light"] ::-webkit-scrollbar-thumb:hover {
  background: #00C957; /* 浅色模式霓虹绿 */
  box-shadow: 0 0 10px #00C957;
}

/* --- 亮色主题 --- */
body[theme-mode="light"] {
  background-image: url('file:///D:/SteamLibrary/steamapps/workshop/content/431960/3045994078/preview.jpg') !important;
  background-color: rgba(255,255,255,0.5) !important;
  background-blend-mode: lighten !important;

  --message-bgcolor: rgba(244, 244, 244, .5);
  --content-bgcolor: rgba(255, 255, 255, 1);
  --content-bgcolor-hard: rgba(255, 255, 255, .6);
  --content-bgcolor-soft: rgba(255, 255, 255, .4);
  --content-bgcolor-soft-soft: rgba(255, 255, 255, .2);
  
  --color-text: #000000 !important; 
  --content-color: #000000 !important;
  color: #000000 !important;

  --theme-color: rgb(59, 130, 246);
  --theme-color-soft: rgba(59, 130, 246, .4);
  --theme-color-hard: rgba(59, 130, 246, .7);

  --modal-background: var(--content-bgcolor-soft);
  --color-background-mute: var(--content-bgcolor-soft);
  --color-border: var(--content-bgcolor-soft-soft);
  --color-background: transparent;
  --color-background-soft: var(--content-bgcolor-soft);
  --navbar-background: unset;
}

/* --- 暗色主题 --- */
body[theme-mode="dark"] {
  background-image: url('file:///D:/SteamLibrary/steamapps/workshop/content/431960/3323190978/preview.jpg') !important;
  background-color: rgba(0,0,0,0.65) !important;
  background-blend-mode: darken !important;

  --message-bgcolor: rgba(40, 44, 52, .7);
  --content-bgcolor: rgba(33, 33, 33, 1);
  --content-bgcolor-soft: rgba(33, 33, 33, .3);
  --content-bgcolor-soft-soft: rgba(33, 33, 33, .2);
  --content-bgcolor-hard: rgba(33, 33, 33, .6);
  
  --color-text: #F0F5F0 !important;

  --theme-color: rgb(7, 52, 242);
  --theme-color-soft: rgba(7, 52, 242, .4);
  --theme-color-hard: rgba(7, 52, 242, .7);

  --modal-background: var(--content-bgcolor-soft);
  --color-background-mute: var(--content-bgcolor-soft);
  --color-border: var(--content-bgcolor-soft-soft);
  --color-background: transparent;
  --color-background-soft: var(--content-bgcolor-soft);
  --navbar-background: unset;
}

/* --- 输入框黑紫霓虹 + 毛玻璃背景融合 --- */
#inputbar {
  z-index: 1;
  position: relative;
  box-shadow: var(--box-shadow);
  margin: 0 15px 15px 15px !important;
  background-color: var(--content-bgcolor-hard) !important;
  backdrop-filter: var(--blur) !important;
  border-radius: 15px;
  transition: box-shadow 0.3s ease;
}

#inputbar::before {
  content: '';
  position: absolute;
  inset: -2px; /* 稍微加宽一点边框 */
  border-radius: inherit;
  padding: 2px;
  /* 修复：移除极暗的黑色，使用连续的紫绿渐变，防止浅色模式下暗部看起来像断层/没到达边缘 */
  background: linear-gradient(90deg, #5e0099, #b829ff, #00C957, #b829ff, #5e0099); 
  background-size: 200% 200%;
  mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
  mask-composite: exclude;
  animation: gradientFlow 3s linear infinite; /* 稍微加快流动速度 */
  opacity: 0;
  transition: all 0.4s ease-in-out;
  pointer-events: none;
}

#inputbar:focus-within {
  animation: blinking 3s linear infinite;
}

#inputbar:focus-within::before {
  opacity: 1;
}

/* 【关键修复】大幅增强深色模式下输入框的发光强度 */
[theme-mode='dark'] #inputbar:focus-within {
  /* 增加底部的深紫与荧光绿混合外发光 */
  box-shadow: 0 0 20px rgba(184, 41, 255, 0.4), 0 0 8px rgba(0, 201, 87, 0.2) !important;
}
[theme-mode='dark'] #inputbar:focus-within::before {
  opacity: 1 !important; /* 解除原本0.5的透明度限制 */
  filter: brightness(1.4); /* 强制提亮霓虹边框1.4倍 */
}

/* =========================================================
   BlurBerry 主题基础组件UI覆盖 (按钮、输入框等)
   ========================================================= */
.ant-btn-primary { background-color: var(--theme-color-hard) !important; backdrop-filter: var(--blur); border: none; }
.ant-btn-primary:hover, .ant-btn-primary:focus { background-color: var(--theme-color-soft) !important; }
.ant-btn-default { background-color: var(--content-bgcolor-soft); backdrop-filter: var(--blur); border: none; }
.ant-btn-default:hover, .ant-btn-default:focus { background-color: var(--content-bgcolor-hard) !important; }
.ant-btn-text:hover, .ant-btn-text:focus { background-color: var(--content-bgcolor-hard); }
.ant-btn-dangerous { border-color: var(--danger-color) !important; background-color: var(--danger-color-soft) !important; backdrop-filter: var(--blur); }
.ant-btn-dangerous:hover { border-color: var(--danger-color-soft) !important; background-color: var(--danger-color-hard) !important; }
.ant-btn-dangerous.ant-btn-primary { background-color: var(--danger-color) !important; border-color: var(--danger-color) !important; color: #fff !important; }

.ant-input-outlined, .ant-input-affix-wrapper:not(.ant-input-textarea-affix-wrapper), .ant-input-number, .ant-picker, .ant-select .ant-select-selector, .ant-select-dropdown, .ant-mentions {
  background-color: var(--content-bgcolor-soft) !important; backdrop-filter: var(--blur); transition: background-color 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
}
.ant-input-outlined:hover, .ant-input-outlined:focus, .ant-input-affix-wrapper:not(.ant-input-textarea-affix-wrapper):hover, .ant-input-affix-wrapper:not(.ant-input-textarea-affix-wrapper):focus, .ant-input-number:hover, .ant-input-number:focus, .ant-picker:hover, .ant-picker:focus, .ant-select .ant-select-selector:hover, .ant-select .ant-select-selector:focus, .ant-select-dropdown:hover, .ant-select-dropdown:focus, .ant-mentions:hover, .ant-mentions:focus {
  border-color: var(--content-bgcolor); background-color: var(--content-bgcolor-hard) !important; box-shadow: var(--box-shadow);
}
.ant-input-affix-wrapper>input.ant-input, .ant-input-affix-wrapper>textarea.ant-input { background-color: transparent !important; }
.ant-input-borderless, .ant-input-borderless:hover, .ant-input-borderless:focus, .ant-input-borderless-focused { border-color: transparent !important; box-shadow: none !important; }
.ant-select-focused .ant-select-selector, .ant-picker-focused, .ant-input-number-focused, .ant-mentions-focused { border-color: var(--content-bgcolor-hard) !important; box-shadow: none !important; }

:where(.css-r9lahv).ant-slider .ant-slider-track { background-color: var(--content-bgcolor-soft) !important; }
:where(.css-r9lahv).ant-slider .ant-slider-handle::after { box-shadow: 0 0 0 2px var(--content-bgcolor-soft) !important; }
:where(.css-r9lahv).ant-slider:hover .ant-slider-track { background-color: var(--content-bgcolor-hard) !important; }
:where(.css-r9lahv).ant-slider:hover .ant-slider-handle::after { box-shadow: 0 0 0 2px var(--content-bgcolor-hard) !important; }
:where(.css-r9lahv).ant-slider:hover .ant-slider-dot-active { border-color: var(--content-bgcolor-hard) !important; }
:where(.css-r9lahv).ant-slider .ant-slider-handle:hover::after, :where(.css-r9lahv).ant-slider .ant-slider-handle:active::after, :where(.css-r9lahv).ant-slider .ant-slider-handle:focus::after { box-shadow: 0 0 0 2.5px var(--content-bgcolor-hard) !important; outline: 6px solid var(--content-bgcolor-hard); }

.ant-tabs-tab.ant-tabs-tab-active .ant-tabs-tab-btn { color: var(--content-bgcolor-soft) !important; }
.ant-tabs-ink-bar { background-color: var(--content-bgcolor-soft) !important; }
.ant-tabs-tab:hover { color: var(--content-bgcolor-hard) !important; }
.ant-menu-item-selected { color: var(--content-bgcolor-hard) !important; }
.ant-menu-item:hover, .ant-menu-submenu-title:hover { color: var(--content-bgcolor-soft) !important; }

.ant-segmented { backdrop-filter: var(--blur); background-color: var(--content-bgcolor-soft-soft); }
.ant-segmented .ant-segmented-item-selected { background: var(--content-bgcolor-soft) !important; z-index: 1 !important; }
.ant-segmented .ant-segmented-item-selected .ant-segmented-item-label { position: relative !important; z-index: 2 !important; }
.ant-segmented .ant-segmented-thumb { background: var(--content-bgcolor-hard) !important; z-index: 0 !important; }
.ant-segmented .ant-segmented-item-selected:hover { background: var(--content-bgcolor-soft) !important; }
.ant-segmented .ant-segmented-group { border-color: var(--content-bgcolor-soft) !important; }

.ant-pagination-item-active { border-color: var(--content-bgcolor-soft) !important; }
.ant-pagination-item-active a { color: var(--content-bgcolor-soft) !important; }
.ant-progress-bg { background-color: var(--content-bgcolor-soft) !important; }
.ant-badge-status-processing { background-color: var(--content-bgcolor-soft) !important; }
.ant-badge-status-processing::after { border-color: var(--content-bgcolor) !important; }
.ant-tree-checkbox-checked .ant-tree-checkbox-inner { background-color: var(--content-bgcolor-soft) !important; border-color: var(--content-bgcolor-soft) !important; }
.ant-tree-node-selected { background-color: var(--content-bgcolor-hard) !important; }
.ant-tag { background-color: var(--content-bgcolor-soft); backdrop-filter: var(--blur); }
.ant-upload { backdrop-filter: var(--blur); }
.ant-tooltip { --antd-arrow-background-color: rgba(33, 33, 33, .6) !important; }
.ant-tooltip .ant-tooltip-inner { background-color: rgba(33, 33, 33, .6); }
.ant-modal-root .ant-modal-mask { background-color: transparent; }
.ant-modal .ant-modal-content { background-color: var(--content-bgcolor-soft); backdrop-filter: var(--blur); }
.ant-modal .ant-modal-header { background-color: unset; }
.ant-dropdown { background-color: var(--content-bgcolor-soft-soft); }
.ant-dropdown .ant-dropdown-menu, .ant-dropdown-menu-submenu .ant-dropdown-menu { background-color: var(--content-bgcolor-soft-soft); backdrop-filter: var(--blur); }
.ant-dropdown-menu-submenu { background-color: transparent; }

/* =========================================================
   应用特定页面和组件 
   ========================================================= */
div[class^="SettingContainer"] { background-color: transparent; border: none; }
div[class^="SettingContainer"] [class^="SettingGroup"] { background-color: var(--content-bgcolor-soft); backdrop-filter: var(--blur); border: none; }
[class^="SettingMenus"] { backdrop-filter: var(--blur); border: none; }
div[class^="SettingContent"] [class^="ProviderListContainer"] { backdrop-filter: var(--blur); }
.ant-collapse { -webkit-backdrop-filter: var(--blur); backdrop-filter: var(--blur); background-color: var(--content-bgcolor-soft) !important; }

/* 修复：将所有列表、菜单项的背景渐变改为从左到右(90deg)，确保浅色模式下完美到达最左侧 */
div[class^="ProviderList"] div[class^="ProviderListItem"],
ul[class^="SettingMenus"] li[class^="MenuItem"],
div[class^="SettingContent"] div[class^="MenuList"] div[class^="ListItemContainer"] {
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
  background-image: linear-gradient(90deg, var(--content-bgcolor-soft-soft) 0%, transparent 100%);
}
div[class^="ProviderList"] div[class^="ProviderListItem"]:hover, ul[class^="SettingMenus"] li[class^="MenuItem"]:hover, div[class^="SettingContent"] div[class^="MenuList"] div[class^="ListItemContainer"]:hover {
  box-shadow: var(--box-shadow); background-color: var(--content-bgcolor-soft); transition: unset;
}
div[class^="ProviderList"] div[class^="ProviderListItem"].active, ul[class^="SettingMenus"] li[class^="MenuItem"].active, div[class^="SettingContent"] div[class^="MenuList"] div[class^="ListItemContainer"].active {
  background-color: var(--content-bgcolor-hard); box-shadow: var(--box-shadow);
}

div[class^="ServerCard"], div[class^="ResourceCard"] { background-color: var(--content-bgcolor-soft-soft); backdrop-filter: var(--blur); }
div[class^="SettingContent"] div[class^="MenuList"] { backdrop-filter: var(--blur); }
div[class^="AssistantContainer"] div[class^="Container"] { background-color: var(--content-bgcolor-soft) !important; }

/* ==========================================
   特效1：AI 消息气泡玻璃化 + 悬浮能量流转
   ========================================== */
.message-assistant {
  background-color: var(--content-bgcolor-hard);
  backdrop-filter: var(--blur);
  padding: 18px 20px 10px 20px !important;
  border-radius: 15px;
  position: relative; /* 为伪元素定位 */
}
.message-assistant::after {
  content: '';
  position: absolute;
  inset: -1.5px;
  border-radius: inherit;
  padding: 1.5px;
  background: linear-gradient(90deg, transparent, #b829ff, #00C957, transparent);
  background-size: 200% 100%;
  mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
  mask-composite: exclude;
  opacity: 0;
  transition: opacity 0.4s ease;
  pointer-events: none;
}
.message-assistant:hover::after {
  opacity: 1;
  animation: aiEnergyFlow 2.5s linear infinite;
}

.messages-container .system-prompt {
  background-color: var(--content-bgcolor-soft);
  backdrop-filter: var(--blur);
}

/* ==========================================
   特效4：用户气泡玻璃化 + 悬浮全息镭射扫光
   ========================================== */
.bubble:not(.multi-select-mode) .message-user .message-content-container {
  background-color: var(--content-bgcolor-soft);
  backdrop-filter: var(--blur);
  position: relative;
  overflow: hidden; /* 限制扫光在气泡内 */
}
.bubble:not(.multi-select-mode) .message-user .message-content-container::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 60%;
  height: 100%;
  background: linear-gradient(120deg, transparent, rgba(255, 255, 255, 0.5), transparent);
  transform: skewX(-25deg);
  pointer-events: none;
}
.bubble:not(.multi-select-mode) .message-user .message-content-container:hover::after {
  animation: holoFoil 0.7s ease-out;
}

/* ==========================================
   特效5：Markdown 代码块极客觉醒
   ========================================== */
.markdown { font-family: "undefined"; font-weight: normal; }
.markdown pre {
  border-radius: 16px;
  background-color: var(--content-bgcolor-soft-soft);
  box-shadow: var(--box-shadow);
  transition: background-color 0.3s ease, box-shadow 0.3s ease;
}
.markdown pre .shiki { background-color: transparent !important; }
.iztnTo:not(:has(+ [class*="Container"])) { border-radius: 0 0 16px 16px; }
.markdown pre [class^="CodeHeader"] { justify-content: center; position: relative; }

/* 默认状态：暗淡的交通灯 */
.markdown pre [class^="CodeHeader"]::before {
  content: '';
  display: block;
  position: absolute;
  top: 50%;
  left: 15px;
  transform: translateY(-50%);
  width: 12px;
  height: 12px;
  border-radius: 50%;
  box-shadow: 20px 0 0 0 rgba(255, 189, 46, 0.4), 40px 0 0 0 rgba(39, 201, 63, 0.4);
  background-color: rgba(255, 95, 86, 0.4);
  border: 0.5px solid rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
  transition: all 0.3s ease;
}
/* 复制按钮默认隐藏/半透明 */
.markdown pre [class^="CodeHeader"] > div:not(:first-child),
.markdown pre [class^="CodeHeader"] button {
  opacity: 0.3;
  transition: all 0.3s ease;
}

/* 觉醒状态：鼠标移入代码块 */
.markdown pre:hover {
  background-color: var(--content-bgcolor-soft);
  box-shadow: 0 4px 20px rgba(0,0,0,0.25);
}
/* 交通灯爆亮 */
.markdown pre:hover [class^="CodeHeader"]::before {
  box-shadow: 20px 0 0 0 #FFBD2E, 40px 0 0 0 #27C93F, 0 0 8px #FF5F56, 20px 0 8px #FFBD2E, 40px 0 8px #27C93F;
  background-color: #FF5F56;
}
/* 复制按钮显现 */
.markdown pre:hover [class^="CodeHeader"] > div:not(:first-child),
.markdown pre:hover [class^="CodeHeader"] button {
  opacity: 1;
}
/* 复制按钮赛博故障悬停 */
.markdown pre [class^="CodeHeader"] > div:not(:first-child):hover,
.markdown pre [class^="CodeHeader"] button:hover {
  animation: glitch 0.2s linear infinite;
  color: #00C957; /* 悬停变为黑客绿 */
}

/* ==========================================
   特效2：侧边栏霓虹光剑
   ========================================== */
#app-sidebar { position: relative; }
#app-sidebar::before {
  content: ""; width: 103%; height: 100%; z-index: -1; position: absolute; backdrop-filter: var(--blur);
}
#app-sidebar div[class^="Icon"] {
  position: relative;
  transition: all 0.3s ease;
}
/* 光剑主体 (伪元素) */
#app-sidebar div[class^="Icon"]::before {
  content: '';
  position: absolute;
  left: 0;
  top: 15%;
  height: 70%;
  width: 3px;
  background-color: #b829ff;
  border-radius: 0 4px 4px 0;
  transform: scaleY(0);
  opacity: 0;
  transition: all 0.2s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}
/* 悬浮状态：光剑半出鞘 */
#app-sidebar div[class^="Icon"]:hover { 
  background-color: var(--content-bgcolor-soft); 
  box-shadow: var(--box-shadow); 
}
#app-sidebar div[class^="Icon"]:hover::before {
  transform: scaleY(0.6);
  opacity: 0.6;
  box-shadow: 0 0 8px #b829ff;
}
/* 激活状态：光剑全亮变色 */
#app-sidebar div[class^="Icon"].active { 
  background-color: var(--content-bgcolor-hard); 
  box-shadow: var(--box-shadow); 
}
#app-sidebar div[class^="Icon"].active::before {
  transform: scaleY(1);
  opacity: 1;
  background-color: #00C957;
  box-shadow: 0 0 8px #00C957, 0 0 15px #00C957;
}

/* --- 主页与选项卡 --- */
.home-tabs { backdrop-filter: var(--blur); }

/* 修复：选项卡悬浮与激活的渐变同样改为从左到右(90deg)，贯穿整个元素 */
.assistants-tab div[role="button"] .ant-dropdown-trigger, div[class^="AssistantAddItem"], div[class^="AddTopicButton"], .topics-tab div[role="button"] .ant-dropdown-trigger {
  transition: background-color 0.3s ease, box-shadow 0.3s ease; 
  background-image: linear-gradient(90deg, var(--content-bgcolor-soft-soft) 0%, transparent 100%);
}
.assistants-tab div[role="button"] .ant-dropdown-trigger:hover, div[class^="AssistantAddItem"]:hover, div[class^="AddTopicButton"]:hover, .topics-tab div[role="button"] .ant-dropdown-trigger:hover {
  background-color: var(--content-bgcolor-soft); box-shadow: var(--box-shadow); transition: unset;
}
.assistants-tab div[role="button"] .ant-dropdown-trigger.active, .topics-tab div[role="button"] .ant-dropdown-trigger.active {
  background-color: var(--content-bgcolor-hard); box-shadow: var(--box-shadow);
}

/* --- 智能体、翻译、绘图页面 --- */
div[class*="AgentsGroupList"] { backdrop-filter: var(--blur); }
div[class*="AgentsGroupList"] div[class^="ListItemContainer"] { transition: background-color 0.3s ease; }
div[class*="AgentsGroupList"] div[class^="ListItemContainer"]:hover { background-color: var(--content-bgcolor-soft); box-shadow: var(--box-shadow); }
div[class*="AgentsGroupList"] div[class^="ListItemContainer"].active { background-color: var(--content-bgcolor-hard); box-shadow: var(--box-shadow); }
div[class^="AgentCardContainer"] { background-color: var(--content-bgcolor-soft-soft); backdrop-filter: var(--blur); }
div[class^="InputContainer"]:has(.ant-input-textarea-affix-wrapper) { backdrop-filter: var(--blur); background-color: var(--content-bgcolor-soft); }
div[class^="OutputContainer"]:has([class^="OperationBar"]) { backdrop-filter: var(--blur); }
.ant-radio-button-wrapper-checked:not(.ant-radio-button-wrapper-disabled), .ant-radio-button-wrapper { background-color: var(--content-bgcolor-soft); backdrop-filter: var(--blur); }
div[class^="LoadingContainer"] div[class^="ImagePlaceholder"] { backdrop-filter: var(--blur); border-radius: 15px; }
div[class^="InputContainer"] .ant-input-borderless:not(.ant-input-affix-wrapper, .ant-input-textarea-affix-wrapper) { background-color: var(--content-bgcolor-soft); backdrop-filter: var(--blur); border-radius: 15px; }
div[class^="AppsContainer"] [class^="Container"]:has([class^="AppTitle"]):hover { background-color: var(--content-bgcolor-soft); border-radius: 16px; transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out; box-shadow: var(--box-shadow); }

/* --- 知识库 --- */
div[class^="KnowledgeSideNav"] { backdrop-filter: var(--blur); }
div[class^="KnowledgeSideNav"] div[class^="ListItemContainer"], div[class^="KnowledgeSideNav"] div[class^="AddKnowledgeItem"] { transition: background-color 0.3s ease, box-shadow 0.3s ease; }
div[class^="KnowledgeSideNav"] div[class^="ListItemContainer"]:hover, div[class^="KnowledgeSideNav"] div[class^="AddKnowledgeItem"]:hover { background-color: var(--content-bgcolor-soft); box-shadow: var(--box-shadow); }
div[class^="KnowledgeSideNav"] div[class^="ListItemContainer"].active, div[class^="KnowledgeSideNav"] div[class^="AddKnowledgeItem"].active { background-color: var(--content-bgcolor-hard); box-shadow: var(--box-shadow); }
div[class^="FileItemCard"] { backdrop-filter: var(--blur); background-color: var(--content-bgcolor-soft-soft); }

/* --- 顶部导航栏 & 抽屉 --- */
div[class^="TabsBar"] :is(div[class^="Tab-htodQk"], div[class^="AddTabButton"]):hover { background-color: var(--content-bgcolor-soft); box-shadow: var(--box-shadow); }
div[class^="TabsBar"] :is(div[class^="Tab-htodQk"], div[class^="AddTabButton"]).active, .jvPWQP { background-color: var(--content-bgcolor-hard); box-shadow: var(--box-shadow); }
div[class^="RightButtonsContainer"]>*:hover { background-color: var(--content-bgcolor-soft); box-shadow: var(--box-shadow); }
div[class^="RightButtonsContainer"]>*.active, .jYjBXc { background-color: var(--content-bgcolor-hard); box-shadow: var(--box-shadow); }
.ant-drawer .ant-drawer-content { background-color: var(--content-bgcolor-hard) !important; border-top-left-radius: 15px; }

/* --- Tab页面覆盖 --- */
div[class^="TabContent"] {
  .home-tabs { box-shadow: var(--box-shadow); border-radius: 10px; height: calc(100vh - var(--navbar-height) - 6px); }
  .bubble .home-navbar div[class^="Box"] { border-left: 2px solid var(--content-bgcolor-soft-soft); padding-left: 5px; }
  div[class^="KnowledgeSideNav"] { box-shadow: var(--box-shadow); border-radius: 10px; margin-bottom: calc(var(--navbar-height) - 38px); }
  div[class*="AgentsGroupList"] { box-shadow: var(--box-shadow); border-radius: 10px; height: calc(100vh - var(--navbar-height) - 6px); }
  ul[class^="SettingMenus"] { border-radius: 10px; box-shadow: var(--box-shadow); margin-bottom: calc(var(--navbar-height) - 38px); height: calc(100vh - var(--navbar-height) - 6px); }
  div[class^="SettingContent"] { margin-left: 10px; }
  div[class^="ProviderListContainer"] { box-shadow: var(--box-shadow); border-radius: 10px; margin-bottom: 15px; height: calc(100vh - var(--navbar-height) - 6px); }
  div[class^="SettingContent"] div[class^="MenuList"] { box-shadow: var(--box-shadow); border-radius: 10px; margin-bottom: 15px; height: calc(100vh - var(--navbar-height) - 6px); }
}
```
