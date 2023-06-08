# 阅读/优化代码
开发者经常接手别人的代码。质量参差不齐，还会夹在很多奇怪的命名。当我们阅读整体逻辑或者修改逻辑，可能会因为自身阅读的问题造成理解偏差，进一步引发 bug。

如果将这个方法交给 AI 去阅读呢？可以看看效果。

> prompt: 
> 逐行解释下面的代码 + 代码内容， (在这里使用了一段在 github 上面的开源代码进行展示，这段代码是一段定时器相关的内容)。

![image](https://github.com/yzcaimz/chatGPT-prompt-example/assets/5369335/111c3452-8131-4a4a-a336-7d64931689fa)

可以看到 ChatGPT 正确的理解了我们的代码，对代码进行了解释和说明。

但是这时候只是生成了一个整体的说明，并没有对每一行分别进行解释。这时候继续和它对话：
> prompt: 可以在每一行代码上面加上注释，便于我理解吗？

![image](https://github.com/yzcaimz/chatGPT-prompt-example/assets/5369335/07397b9d-ea45-4e16-a8e5-cd31aaf03546)
这时候它会逐行的进行代码标注，便于你对每一行进行理解。如果你接着对它提出一个粗浅的优化需求，它也会照做。
> prompt: 这段代码可以进行重构和优化吗？逻辑有些繁琐。

![image](https://github.com/yzcaimz/chatGPT-prompt-example/assets/5369335/1419670f-5859-4f30-a159-783a08325649)
可以对某一个部分提出更细节的要求，为它提出更好的优化方向。在这里我们提出了关于参数顺序耦合的问题，可以看到 GPT 也理解到了我们的需求，并且做出了对应的优化，如下：
> prompt: children: (isCounting: boolean, durationTime: number, startCount: () => void) => React.ReactNode// 子组件，接收三个参数，返回一个 React 节点这里面的参数太多了，而且对顺序有强依赖，该怎么优化这里？

![image](https://github.com/yzcaimz/chatGPT-prompt-example/assets/5369335/bd943e14-19f1-4f84-aff8-694dc755f45d)
