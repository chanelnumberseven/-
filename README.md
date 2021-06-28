# 工作问题及解决方案汇总

## 如何用css3做抛物线动画

从力学角度上来看，css3其实提供了描述物体运动的六个维度（x,y,z轴的平移和旋转），有了这六个维度，可以描绘一个物体的任何运动状态；比如工作中遇到这样一个问题：当用户添加一个商品时，如何让商品做一个抛物线动画；从物理学角度分析，抛物线运动其实是水平方向的移动和垂直方向的匀加速运动形成的复合运动；实现方案如下：
demo:https://codesandbox.io/s/busy-easley-30gys?file=/src/styles.css

```tsx

import "./styles.css";

export default function App() {
  return (
    <div className="horizontal">
      <div className="vertical" />
    </div>
  );
}

```

```css

.horizontal,
.vertical {
  height: 24px;
  width: 24px;
}
.vertical {
  background-color: red;
}

.horizontal {
  animation: slide 1500ms linear infinite;
}
.vertical {
  animation: slideDown 1500ms cubic-bezier(0.64, 0.01, 1, 0.29) infinite;
}

@keyframes slideDown {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(400px);
  }
}

@keyframes slide {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(400px);
  }
}

```
