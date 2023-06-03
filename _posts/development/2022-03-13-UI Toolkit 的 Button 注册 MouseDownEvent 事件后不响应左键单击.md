---
title: UI Toolkit 的 Button 注册 MouseDownEvent 事件后不响应左键单击
Author: Yanxi Liu
category: Development
---

直接调用 `Button.RegisterCallback` 注册 `MouseDownEvent` 事件时发现这个按钮只会响应右键单击而不响应左键单击。而调用 `Button.clickable.activators.Add()`方法时可以响应左键单击。最后发现原因是后者会阻断左键单击的传播。因此最好是用后者来注册左键单击事件而非前者，不过也可以在调用`RegisterCallback()`之前先调用 `Button.clickable.activators.Clear()`方法来达到这个目的。

    private void RegisterCallbacks() {
        var root = rootVisualElement;
        var button = root.Query<Button>("button").First();
    
        //方法1：
        button.clickable.activators.Clear();
        button.RegisterCallback<MouseDownEvent>(MyOnMouseDown1);
    
        //方法2：
        button.clickable.activators.Add(new ManipulatorActivationFilter { button = MouseButton.LeftMouse });
        button.clicked += MyOnMouseDown2;
    }
    
    private void MyOnMouseDown1(MouseDownEvent evt){
        //Do something
    }
    
    private void MyOnMouseDown2(){
        //Do something
    }