---
title: Spatial UI Converter
Author: Yanxi Liu
category: Project
---

Spatial UI Converter是一个可以将 Unity UI Toolkit 生成的 VisualElements 转化成对应的 Mixed Reality Toolkit 的 Prefab 供 MR 程序使用。UI Toolkit 是一套类似于前端HTML和CSS的UI工具。

这个工具的初衷是我们发现直接拖动预制体来做3D的UI特别费劲。首先是3D的GameObject在调整大小上本身就不如使用RectTranform来的方便，其次是调整合适的Z值也很麻烦，因此我就做了这个工具。只需要将UI Toolkit的UI Document（UXML和USS）添加到Spatial UI Converter的ScriptableObject上然后直接转换就可以，使用起来也十分方便。

以下是支持的控件和对应的MRTK2控件

- Button: PressableButtonHoloLens2
- Toggle: PressableButtonHoloLens2Toggle (with its variants, depending on toggle types)
- Label: UITextSelawik (with TextMeshPro instead of TextMesh)
- Slider: PinchSlider
- SliderInt: StepSlider
- TextField: MRKeyboardInputField_TMP
- ScrollView: Scrolling Object Collection
- Foldout: Object Collection
- VisualElement (i.e. not any of the other controls, you can also use an empty VisualElement to tune the layout.)

![截图](https://yanxi-kritia.com/wp-content/uploads/2023/06/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE-2023-06-03-102412.png)