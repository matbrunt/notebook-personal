# Neural networks as the next evolution of software

Interesting article from Andrej Karpathy, the director of AI at Tesla, with his ideas on potentially the next evolution in software - what he dubs '*Software 2.0*'. The majority of this post is simply paraphrasing parts that I found interesting, so I would highly recommend reading the [original article](https://medium.com/@karpathy/software-2-0-a64152b37c35).

> If you think of neural networks as a software stack and not just a pretty good classifier, it becomes quickly apparent that they have a huge number of advantages and a lot of potential for transforming software in general.

> Neural networks are not just another classifier, they represent the beginning of a fundamental shift in how we write software.

> Software 2.0 is written in neural network weights.

> we specify some constraints on the behavior of a desirable program (e.g., a dataset of input output pairs of examples) and use the computational resources at our disposal to search the program space for a program that satisfies the constraints.

> In the case of neural networks, we restrict the search to a continuous subset of the program space where the search process can be made (somewhat surprisingly) efficient with backpropagation and stochastic gradient descent.

> A large portion of programmers of tomorrow do not maintain complex software repositories, write intricate programs, or analyze their running times. They collect, clean, manipulate, label, analyze and visualize data that feeds neural networks.

> Software 2.0 is not going to replace 1.0 (indeed, a large amount of 1.0 infrastructure is needed for training and inference to “compile” 2.0 code), but it is going to take over increasingly large portions of what Software 1.0 is responsible for today.

> Google is currently at the forefront of re-writing large chunks of itself into Software 2.0 code. “[One model to rule them all](https://arxiv.org/abs/1706.05137)” provides an early sketch of what this might look like, where the statistical strength of the individual domains is amalgamated into one consistent understanding of the world.

The variety of application right now is still very narrow, unlike raw text / speech / images, applications on 'structured' data haven't had a lot of new discoveries, but hopefully this will change soon as it becomes a more visible implementation.

One of my colleagues came up with interesting applications where we can train a neural network to automatically reverse engineer and generate code for algorithms given known inputs / outputs, for example, writing a crawler that updates itself every time a page structure changes.

## Examples of this ongoing transition

**Visual Recognition** used to consist of engineered features with a bit of machine learning sprinkled on top at the end (e.g., SVM). Since then, we developed the machinery to discover much more powerful image analysis programs (in the family of ConvNet architectures), and more recently we’ve begun [searching over architectures](https://arxiv.org/abs/1703.01041).

**Speech recognition** used to involve a lot of preprocessing, gaussian mixture models and hidden markov models, but [today](https://github.com/syhw/wer_are_we) consist almost entirely of neural net stuff.

**Speech synthesis** has historically been approached with various stitching mechanisms, but today the state of the art models are large convnets (e.g. [WaveNet](https://deepmind.com/blog/wavenet-launches-google-assistant/)) that produce raw audio signal outputs.

**Machine Translation** has usually been approaches with phrase-based statistical techniques, but neural networks are quickly becoming dominant. My favorite architectures are trained in the [multilingual setting](https://arxiv.org/abs/1611.04558), where a single model translates from any source language to any target language, and in weakly supervised (or entirely [unsupervised](https://arxiv.org/abs/1710.11041)) settings.

**Robotics** has a long tradition of breaking down the problem into blocks of sensing, pose estimation, planning, control, uncertainty modeling etc., using explicit representations and algorithms over intermediate representations. We’re not quite there yet, but research at [UC Berkeley](https://www.bloomberg.com/features/2015-preschool-for-robots/) and [Google](https://research.googleblog.com/2016/03/deep-learning-for-robots-learning-from.html) hint at the fact that Software 2.0 may be able to do a much better job of representing all of this code.

**Games**. Go playing programs have existed for a long while, but [AlphaGo Zero](https://deepmind.com/blog/alphago-zero-learning-scratch/) (a ConvNet that looks at the raw state of the board and plays a move) has now become by far the strongest player of the game. I expect we’re going to see very similar results in other areas, e.g. [DOTA 2](https://blog.openai.com/more-on-dota-2/), or [StarCraft](https://deepmind.com/blog/deepmind-and-blizzard-open-starcraft-ii-ai-research-environment/).

## The benefits

Using a ConvNet compared to a production C++ code base, the ConvNet works better in practice than complex programs, and is simpler. A typical neural network is essentially just two operations - matrix multiplication and thresholding at zero (ReLU). Because you only need a smaller amount of code for the core computational functions such as matrix multiply, it is a lot easier to build performant and low error code.

Another advantage of this is because we have a smaller instruction set, we can take advantage of advances in technology that make small, inexpensive, low-powered chips readily available and bundle neural networks with the chips. For example with each chip provide a pre-trained ConvNet, a speech recogniser, and a WaveNet speech synthesis network, all integrated in a small protobrain that can be attached to anything.

It is easier to optimise the function of the network as well - every iteration of a typical neural net forward pass takes exactly the same amount of FLOPS, with no variability based on the different execution paths the code could take through a C++ code base. Dynamic compute graphs will be different, but execution flow is still significantly constrained, making it harder to end up in unintended infinite loops. This also leads to consistent memory use, as there is no dynamically allocated memory we can reduce the requirement to swap to disk, or end up with memory leaks that take time and effort to track down.

With the simpler underlying structure of matrix multiplication we can apply this architecture more easily across platforms, compared to the arbitrary configurations requried for classical binary and script distribution.

We can make substantial changes to the application quicker and with less effort. If you want to increase the performance, compared to having to go through a complex code base with a neural network you would just remove half of the channels, retrain the model and it runs at twice the speed with slightly worse accuracy. If we get access to better computation power or more data, then we can immediately realise gains in the application by just adding more channels and retraining.

Neural networks can be constructed as building blocks and more easily plugged together. Software architectures are decomposed into modules that communicate through interfaces such as public functions, APIs and endpoints. However if two Software 2.0 modules that were originally trained seperately interact, we can easily backpropagate through the whole.

This has a high number of applications, for example imagine if your web browser could automatically redesign its low level system instructions near the bottom of the stack to more efficiently load web pages.

There is a lower barrier to entry as well - the underlying concepts just require basic linear algebra, calculus, Python and some CS231n lectures. This makes it easier to learn, however the complexity curve rapidly rises so will also reward experience and intuition built up over time.

On the current applications neural networks are outperforming people in some areas, such as images/video, sound/speech and text.

## Current limitations

One of the largest issues is with the large neural networks, we have good accuracy in our models, but with no idea how they work, which is a concern in itself and open to abuse.

> Across many applications areas, we’ll be left with a choice of using a 90% accurate model we understand, or 99% accurate model we don’t.

This stack can also fail in [unintuitive and embarrassing ways](https://motherboard.vice.com/en_us/article/nz7798/weve-already-taught-artificial-intelligence-to-be-racist-sexist),or worse, they can “silently fail”, for example by silently adopting biases in their training data, which are very difficult to properly analyze and examine when their sizes are easily in the millions in most cases.

The inability to understand how the models work also brings some interesting avenues to explore, for instance the existence of [adversarial examples](https://blog.openai.com/adversarial-example-research/) and [attacks](https://github.com/yenchenlin/awesome-adversarial-machine-learning).

## References

[Software 2.0](https://medium.com/@karpathy/software-2-0-a64152b37c35)

[Deep learning is eating software](https://petewarden.com/2017/11/13/deep-learning-is-eating-software/)