[TOC]

## stable-diffusion

### 使用ChatGPT生成相关tags

```markdown
# Stable Diffusion prompt 助理

你来充当一位有艺术气息的Stable Diffusion prompt 助理。

## 任务

我用自然语言告诉你要生成的prompt的主题，你的任务是根据这个主题想象一幅完整的画面，然后转化成一份详细的、高质量的prompt，让Stable Diffusion可以生成高质量的图像。

## 背景介绍

Stable Diffusion是一款利用深度学习的文生图模型，支持通过使用 prompt 来产生新的图像，描述要包含或省略的元素。

## prompt 概念

- 完整的prompt包含“**Prompt:**”和"**Negative Prompt:**"两部分。
- prompt 用来描述图像，由普通常见的单词构成，使用英文半角","做为分隔符。
- negative prompt用来描述你不想在生成的图像中出现的内容。
- 以","分隔的每个单词或词组称为 tag。所以prompt和negative prompt是由系列由","分隔的tag组成的。

## () 和 [] 语法

调整关键字强度的等效方法是使用 () 和 []。 (keyword) 将tag的强度增加 1.1 倍，与 (keyword:1.1) 相同，最多可加三层。 [keyword] 将强度降低 0.9 倍，与 (keyword:0.9) 相同。

## Prompt 格式要求

下面我将说明 prompt 的生成步骤，这里的 prompt 可用于描述人物、风景、物体或抽象数字艺术图画。你可以根据需要添加合理的、但不少于5处的画面细节。

### 1. prompt 要求

- 你输出的 Stable Diffusion prompt 以“**Prompt:**”开头。
- prompt 内容包含画面主体、材质、附加细节、图像质量、艺术风格、色彩色调、灯光等部分，但你输出的 prompt 不能分段，例如类似"medium:"这样的分段描述是不需要的，也不能包含":"和"."。
- 画面主体：不简短的英文描述画面主体, 如 A girl in a garden，主体细节概括（主体可以是人、事、物、景）画面核心内容。这部分根据我每次给你的主题来生成。你可以添加更多主题相关的合理的细节。
- 对于人物主题，你必须描述人物的眼睛、鼻子、嘴唇，例如'beautiful detailed eyes,beautiful detailed lips,extremely detailed eyes and face,longeyelashes'，以免Stable Diffusion随机生成变形的面部五官，这点非常重要。你还可以描述人物的外表、情绪、衣服、姿势、视角、动作、背景等。人物属性中，1girl表示一个女孩，2girls表示两个女孩。
- 材质：用来制作艺术品的材料。 例如：插图、油画、3D 渲染和摄影。 Medium 有很强的效果，因为一个关键字就可以极大地改变风格。
- 附加细节：画面场景细节，或人物细节，描述画面细节内容，让图像看起来更充实和合理。这部分是可选的，要注意画面的整体和谐，不能与主题冲突。
- 图像质量：这部分内容开头永远要加上“(best quality,4k,8k,highres,masterpiece:1.2),ultra-detailed,(realistic,photorealistic,photo-realistic:1.37)”， 这是高质量的标志。其它常用的提高质量的tag还有，你可以根据主题的需求添加：HDR,UHD,studio lighting,ultra-fine painting,sharp focus,physically-based rendering,extreme detail description,professional,vivid colors,bokeh。
- 艺术风格：这部分描述图像的风格。加入恰当的艺术风格，能提升生成的图像效果。常用的艺术风格例如：portraits,landscape,horror,anime,sci-fi,photography,concept artists等。
- 色彩色调：颜色，通过添加颜色来控制画面的整体颜色。
- 灯光：整体画面的光线效果。

### 2. negative prompt 要求
- negative prompt部分以"**Negative Prompt:**"开头，你想要避免出现在图像中的内容都可以添加到"**Negative Prompt:**"后面。
- 任何情况下，negative prompt都要包含这段内容："nsfw,(low quality,normal quality,worst quality,jpeg artifacts),cropped,monochrome,lowres,low saturation,((watermark)),(white letters)"
- 如果是人物相关的主题，你的输出需要另加一段人物相关的 negative prompt，内容为：“skin spots,acnes,skin blemishes,age spot,mutated hands,mutated fingers,deformed,bad anatomy,disfigured,poorly drawn face,extra limb,ugly,poorly drawn hands,missing limb,floating limbs,disconnected limbs,out of focus,long neck,long body,extra fingers,fewer fingers,,(multi nipples),bad hands,signature,username,bad feet,blurry,bad body”。

### 3. 限制：
- tag 内容用英语单词或短语来描述，并不局限于我给你的单词。注意只能包含关键词或词组。
- 注意不要输出句子，不要有任何解释。
- tag数量限制40个以内，单词数量限制在60个以内。
- tag不要带引号("")。
- 使用英文半角","做分隔符。
- tag 按重要性从高到低的顺序排列。
- 我给你的主题可能是用中文描述，你给出的prompt和negative prompt只用英文。

我的第一个主题是： 一个美丽的中国女孩
```

### 模型

#### 二次元模型

1. **TMND-Mix**

   Suggestion/建议:

   Step 1/第1步: txt2img/文生图:

   Negative prompt: (worst quality:2), (low quality:2), (normal quality:2)

   Sampling steps/迭代步数: 40-50

   Hires. fix/高分辨率修复: On/开

   Upscaler/放大算法: R-ESRGAN 4x+ or 4x-UltraSharp

   Hires steps/高分迭代步数: 20

   Denoising strength/重绘幅度: 0.2-0.4

    

   Step 2/第2步: Send to img2img/>> 图生图:

   Resize mode/缩放模式: Just resize/仅调整大小

   Denoising strength/重绘幅度: 0.2-0.25

   Script/脚本: SD upscale/使用SD放大(Upscaler/放大算法:R-ESRGAN 4x+ or 4x-UltraSharp)

2. **AbyssOrangeMix3 (AOM3)**

   How to use:

   Prompts

   Negative prompts is As simple as possible is good.

   (worst quality, low quality:1.4)

   Using "3D" as a negative will result in a rough sketch style at the "sketch" level. Use with caution as it is a very strong prompt.

    

   How to avoid Real Face

   (realistic, lip, nose, tooth, rouge, lipstick, eyeshadow:1.0), (abs, muscular, rib:1.0),

    

   How to avoid Bokeh

   (depth of field, bokeh, blurry:1.4)

    

   🔰Basic negative prompts sample for Anime girl ↓

   v1

   nsfw, (worst quality, low quality:1.4), (realistic, lip, nose, tooth, rouge, lipstick, eyeshadow:1.0), (dusty sunbeams:1.0),, (abs, muscular, rib:1.0), (depth of field, bokeh, blurry:1.4),(motion lines, motion blur:1.4), (greyscale, monochrome:1.0), text, title, logo, signature

   v2

   nsfw, (worst quality, low quality:1.4), (lip, nose, tooth, rouge, lipstick, eyeshadow:1.4), ( jpeg artifacts:1.4), (depth of field, bokeh, blurry, film grain, chromatic aberration, lens flare:1.0), (1boy, abs, muscular, rib:1.0), greyscale, monochrome, dusty sunbeams, trembling, motion lines, motion blur, emphasis lines, text, title, logo, signature,

   Sampler: Take your pick

    

   Steps: 

   DPM++ SDE Karras: Test: 12～ ,illustration: 20～

   DPM++ 2M Karras: Test: 20～ ,illustration: 28～

   Clipskip: 1 or 2

   Upscaler :

   Detailed illust → Latenet (nearest-exact)

   Denoise strength: 0.5 (0.5~0.6)

   Simple upscale: Swin IR, ESRGAN, Remacri etc…

   Denoise strength: Can be set low. (0.35~0.6)

3. **Anything XL**

   If you want to generate high-quality pictures, you can use negative prompts, such as:

   如果要生成高质量的图片，可以使用否定提示，例如：

    

   nsfw, lowres, bad anatomy, bad hands, text, error, missing fingers, extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts, signature, watermark, username, blurry, artist name

   Negative tags can include common negative tags, but it is best not to assign too high of a weight to their content, for example (ugly:2.8).

   否定标签可以包含常见的否定标签，但最好不要为其内容分配太高的权重，例如 （ugly：2.8）。

    

   Because of models merge, some labels in the original model that have not been fully trained may be lost, and some labels may need to have a weight of over 1.5 in order to be effective.

   由于模型合并，原始模型中一些尚未完全训练的标签可能会丢失，并且某些标签可能需要权重超过 1.5 才能生效。

    

   Resolution： 分辨率：

   A resolution greater than 1024×1024 is recommended, and hires fix is recommended if you want higher resolution or quality

   建议使用大于 1024×1024 的分辨率，如果您想要更高的分辨率或质量，建议使用 hires fix

    

   Most of the generation parameters of the example graph are:

   示例图的大多数生成参数是：

   > euler_a | 20steps | no hires fix | CFG7
   >
   > 2048 x 2048   not recommended
   >
   > ……
   >
   > 1280 x 2048   
   >
   > 1280 x 1536   
   >
   > 960 x 1536   Recommended
   >
   > 1024 x 1024   1:1  Square
   >
   > …… 
   >
   > 960 x 640        
   >
   > 768 x 512   SD1.5
   >
   > ……
   >
   > 2048 x 512   Unable to guarantee the quality
   >
   > 512 x 2048   Unable to guarantee the quality

### 参数介绍

#### Prompts

本文示例都是用的 [ReV Animated V1.2.2](https://civitai.com/models/7371/rev-animated) 模型， 参数是 [stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) 的默认参数。

- https://civitai.com/models/7371/rev-animated
- https://github.com/AUTOMATIC1111/stable-diffusion-webui

##### 提示词一定要用中文么？

我们用**一个苹果放在桌子上**中英文来做提示词看生成的效果，

从下面两幅图可以看到，中文根本不知道生成的是啥，英文满足我们的期望。

> 一个苹果放在桌子上

竟然画出了这个
![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940312-1703044098.jpg)
一个苹果放在桌子上
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3022276479, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

用英文时

> An apple on the table

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940313-241040785.jpg)
An apple on the table
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3513630856, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 逗号分隔语意tag

使用英文逗号 , 分隔不同的关键词tag，空格和换行等不影响tag分隔。

比如我们用下面关键字来绘画

> 1girl , long hair , low twintails , front ponytail

- “1girl” 是指绘图的主题，通常是指一张只有一个女孩的插画或漫画。
- “long hair” 长头发。
- “low twintails” 是一种发型，是将头发分成两部分，然后在头顶上方的位置绑成两个小辫子的一种发型。
- “front ponytail” 是一种发型，是将头发拉到前面，然后用发带或发夹固定在前额上方的一种发型。这种发型可以让人看起来更加清爽、干净。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940331-233372278.jpg)
1girl , long hair , low twintails , front ponytail
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3958830808, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 要素混合

将 | 加在多个关键词之间，可以实现多个要素的混合。

> 1girl , blue | black hair , low twintails , front ponytail

蓝黑相间的头发

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940314-1641471687.jpg)

1girl , blue | black hair , low twintails , front ponytail
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 4004018812, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

> [cat|tiger]

代表cat和tiger交替绘制，最后能生成虎猫兽。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940339-449338459.jpg)

[cat|tiger]
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3450602202, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

> [cow|donkey|horse|zebra|deer|elephant] in a field

代表牛驴马斑马鹿大象交替绘制，最后生成一个奇怪的四不象。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940362-1410947140.jpg)

[cow|donkey|horse|zebra|deer|elephant] in a field
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 8773839, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 权重

权重会影响生成图片和关键词的联系度，默认的单词顺序就会影响权重，单词顺序越往后，权重越低。

权重数值从0.1~100，默认状态是1，低于1就是减弱，大于1就是加强。

语法糖： () 每用一次代表权重提高 1.1 倍，[] 每用一次代表权重降低 1.1 倍，以此类推。也可以直接在括号里输入冒号后面直接写上权重的数值。

- (word) - 将括号内的提示词权重提高 1.1 倍
- ((word)) - 将括号内的提示词权重提高 1.21 倍 （= 1.1 * 1.1）
- [word] - 将括号内的提示词权重降低 1.1 倍
- (word:1.5) - 将括号内的提示词权重提高 1.5 倍
- (word:0.25) - 将括号内的提示词权重减少4 倍（= 1 / 0.25）

示例

> (1girl : 1.2) , long black hair , (cat ears : 1.1) , (nice_dress : 0.9)

- long black hair 长黑头发
- cat ears 猫耳朵
- nice_dress 连衣裙

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940360-1850871095.jpg)

(1girl : 1.2) , long black hair , (cat ears : 1.1) , (nice_dress : 0.9)
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 2409461809, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 渐变

语法：

> [from:to:when]

先绘制前面的提示词内容(from)，然后再绘制后面的提示词内容(to)，当（when）时转变。

举个例子：

> [beach girl 10]

这种写法中，如果总步数设置为20，前10步渲染关键词beach 沙滩 ，后面10步渲染关键词girl 女孩。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940363-559029860.jpg)

[beach girl 10]
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 1016618029, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

此语法还有两个变体：

> [to:when] - 在设定的步数后开始绘制
> [from::when] - 在设定的步数后结束绘制

当when小于1时，认为是百分比，下面例子，黑白相间各50%的头发：

> 1girl , [white : black : 0.5] hair , low twintails , front ponytail

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940314-592985761.jpg)

1girl , [white : black : 0.5] hair , low twintails , front ponytail
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 1346704297, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 并存

此语法使用大写 AND ，以使两者权重保持一致。
例如下面这个是即像狮子又像熊的动物

> a lion AND a bear

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940336-2131091700.jpg)

a lion AND a bear
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3135028232, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

另外此语法支持指定权重值：默认权重值为 1，也可以指定每个提示词的权重，比如：

> a cat :1.3 AND a dog :1.2 AND a panda :2.6

下面这幅画，更像熊猫，但是也有猫和狗的特征。
![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510082940340-1632872184.jpg)

a cat :1.3 AND a dog :1.2 AND a panda :2.6
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 2243564072, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 总结

提示词prompt语法主要就是各种权重、渐变、混合..., 搞懂了提示词prompt语法，我们在写提示词的时候就可以适当使用上面这些技巧。

#### Negative prompts

反向提示词（Negative prompts）用于描述图片中**不希望出现的内容**。常用于阻止生成特定的事物、样式或修复某些图像异常。

下面是一些例子

##### 从“宁静的精灵森林” 中移除 “苔藓”

宁静的精灵森林

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510172812625-418856074.jpg)

peaceful elven forest, thick forest, large living trees are visible in the background, by alan lee, michal karcz, smooth details, lord of the rings, game of thrones, smooth, detailed terrain, oil painting, trending artstation, concept art, fantasy matte painting
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3376333067, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

去除苔藓效果

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510172812663-598650375.jpg)

peaceful elven forest, thick forest, large living trees are visible in the background, by alan lee, michal karcz, smooth details, lord of the rings, game of thrones, smooth, detailed terrain, oil painting, trending artstation, concept art, fantasy matte painting
Negative prompt: moss
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3376333067, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

去除 “重复”

猫虎兽

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510172812545-1181750008.jpg)

[cat|tiger]
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3450602202, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

上面出现了2只，我们如果期望只出现一只，去除重复。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510172812668-426999524.jpg)

[cat|tiger]
Negative prompt: duplicate
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 419914, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 完全改变图像风格

哥特式幻想山谷，龙，火

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510172812644-970507262.jpg)

a beautiful digital illustration painting of a detailed gothic fantasy valley and forest dragon fire fey unseelie, by benoit b. mandelbrot, steven belledin, martin johnson heade, lee madgwick, caspar david friedrich, and david rios ferreira. 8 k resolution trending on artstation concept art digital illustration
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 312689412, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

排除 黑暗、雾、颗粒后，风格完全变了。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510172812606-945987890.jpg)

a beautiful digital illustration painting of a detailed gothic fantasy valley and forest dragon fire fey unseelie, by benoit b. mandelbrot, steven belledin, martin johnson heade, lee madgwick, caspar david friedrich, and david rios ferreira. 8 k resolution trending on artstation concept art digital illustration
Negative prompt: fog, darkness, grain
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 312689412, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

#### Sampling method

#### Sampling steps

#### Hires. fix

#### Batch count&Batch size

#### CFG Scale

在图像生成过程中，CFG Scale 参数是一个关键因素，它控制着文本提示对生成图像的影响程度。

简而言之CFG Scale ：

- 参数越大，生成的图像与文本提示的相关性越高，但可能会失真。
- 数值越小，相关性则越低，越有可能偏离提示或输入图像，但质量越好。

在实际应用中，将其设置在 7 到 11 之间往往能获得最佳的低噪效果。

值得注意的是，较高的 CFG Scale 数值不仅能提高生成结果与提示的匹配度，还会增加结果图片的饱和度和对比度，使颜色更加平滑，但纹理较少。然而，当数值高于 20 时，生成效果可能会出现反向变化，导致效果变差。

受CFG Scale参数变化影响最大的是连接度高的提示词图， 这意味着图中的单词彼此密切相关。

例如，提示“A photorealistic painting of a cat sitting on a chair”（一只猫坐在椅子上的逼真绘画）的提示词图将具有高度的连接性，因为提示中的所有词都彼此密切相关。

**CFG scale: 1**

CFG Scale = 1：生成的图像是一幅非常有创意的画，一只猫坐在椅子上。 它根本不像提示，模糊，坐姿奇怪、椅子奇怪等。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230511221453655-722541581.jpg)

A photorealistic painting of a cat sitting on a chair
Negative prompt: duplicate
Steps: 20, Sampler: Euler a, CFG scale: 1, Seed: 4104372660, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

**CFG scale: 5**

CFG Scale = 5：生成的图像有创意，且像提示。 猫坐在椅子上，尾巴有点奇怪， 颜色跟下面几个比，有点淡。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230511221453715-647641659.jpg)

A photorealistic painting of a cat sitting on a chair
Negative prompt: duplicate
Steps: 20, Sampler: Euler a, CFG scale: 5, Seed: 4104372660, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

**CFG scale: 7**

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230511221453756-2060312117.jpg)

A photorealistic painting of a cat sitting on a chair
Negative prompt: duplicate
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 4104372660, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

**CFG scale: 10**

CFG Scale = 10：生成的图像开始看起来像提示。 椅子靠背有点奇怪。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230511221453725-1868975495.jpg)

A photorealistic painting of a cat sitting on a chair
Negative prompt: duplicate
Steps: 20, Sampler: Euler a, CFG scale: 10, Seed: 4104372660, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

**CFG scale: 15**

CFG Scale = 15：生成的图像开始看起来像提示，不太可能有任何创意元素。 这只猫坐在逼真的房间里一张逼真的椅子上。

猫的耳朵、眼睛有点不匹配，过于突出了。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230511221453763-980003623.jpg)

A photorealistic painting of a cat sitting on a chair
Negative prompt: duplicate
Steps: 20, Sampler: Euler a, CFG scale: 15, Seed: 4104372660, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

**CFG scale: 20**

CFG Scale = 20：生成的图片看起来和提示的很像，不太可能有什么创意元素。 猫坐在逼真的房间里一张逼真的椅子上，画面非常细腻。

由于噪声多，猫脸，背景会感觉颜色有点突出了。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230511221453693-1554510707.jpg)

A photorealistic painting of a cat sitting on a chair
Negative prompt: duplicate
Steps: 20, Sampler: Euler a, CFG scale: 20, Seed: 4104372660, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

**CFG scale: 30**

CFG Scale = 30： 生成的图完全变了风格。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230511225844891-1231266645.jpg)

A photorealistic painting of a cat sitting on a chair
Negative prompt: duplicate
Steps: 20, Sampler: Euler a, CFG scale: 30, Seed: 1659328295, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

**CFG 音阶的最佳点是什么？**

CFG 比例值介于 0 到 20 之间。一般来说，CFG 比例值介于 7 到 11 之间时会产生最佳的低噪效果。

以下是使用 CFG 的一些建议：

- 从较低的 CFG 比例值开始并增加它，直到您对结果满意为止。
- 对更复杂的提示使用更高的 CFG 比例值。
- 对于您想要更有创意的提示，请使用较低的 CFG 比例值。
- 尝试不同的 CFG 比例值，看看哪种最适合您。

#### Seed

seed 参数允许您指定一个随机种子，将用于初始化图像生成过程。

相同的种子值每次都会产生相同的图像集，这对于再现性和一致性很有用。如果将种子值保留为 -1 ，则每次运行文本-图像特性时将生成一个随机种子。

最重要的是，具有相同参数、prompt 和 seed 将产生完全相同的图像。多亏了这一点，我们可以生成图片的多个**相似变体**（**固定seed，调整prompt来生成不同表情的照片**）。

##### 不同表情的女孩

我们的基本原图是 “一个女孩的肖像” 和 3646265433 种子。

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242163-586465380.jpg)

portrait of a girl
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3646265433, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

1、微笑

增加 “微笑” 提示词

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242289-1157314080.jpg)

portrait of a girl , Smiling
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3646265433, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

2、生气

增加 “生气” 提示词

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242280-241537260.jpg)

portrait of a girl , Angry
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3646265433, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

3、兴奋

增加 “兴奋” 提示词

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242255-1545973309.jpg)

portrait of a girl , Excited
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 3646265433, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 一年四季的公园

1、春天

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242281-491717126.jpg)

park , spring
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 1214639448, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

2、夏天

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242324-1130397552.jpg)

park , summer
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 1214639448, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

3、秋天

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242323-1855864121.jpg)

park , autumn
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 1214639448, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

4、冬天

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242279-1866919647.jpg)

park , winter
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 1214639448, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

##### 不同画风的 Musk

由不同艺术家创作的埃隆·马斯克。

1、文森特·梵高 画风

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242307-7990617.jpg)

painting of elon musk in the style of Vincent van Gogh
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 88989970, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

2、巴勃罗·毕加索 画风

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242193-2097386887.jpg)

painting of elon musk in the style of picasso
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 88989970, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

3、萨尔瓦多达利 画风

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242179-816386113.jpg)

painting of elon musk in the style of Salvador Dalí
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 88989970, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

4、瓦西里·康定斯基 画风

![img](https://img2023.cnblogs.com/blog/120296/202305/120296-20230510214242331-1077926159.jpg)

painting of elon musk in the style of Wassily Kandinsky
Steps: 20, Sampler: Euler a, CFG scale: 7, Seed: 88989970, Size: 512x512, Model hash: 4199bcdd14, Model: revAnimated_v122

#### Script