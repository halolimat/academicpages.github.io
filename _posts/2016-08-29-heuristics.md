---
title:  "Heuristics: the art of good guessing"
date:   2016-08-29 10:51:00
permalink: /2016/heuristics/
tags:
  - intro posts
description: Heuristics explained with a simple numeric minimization problem using Particle swarm optimization technique.
---

Heuristics explained with a simple numeric minimization problem using Particle swarm optimization technique.

In computer science, we find solutions to problems, and one of the tools we use to solve problems is the algorithm. Algorithms are procedures that a computer follows and executes. However, some algorithms are not always the best way to solve certain very complex problems, problems in which a partial or an approximate solution would suffice.

One of the things that I love about computer science is how we use and learn from everything around us and from all fields of study and disciplines. (You can learn more about this in a talk by Kevin Slavin titled [How algorithms shape our world][tedTalk].) In this article, however, I will explain a very simple concept we use to solve very complex problems. It's an idea inspired by the social behavior of animals, such as fish that swim in a school or birds that fly in a flock. And it doesn't involve an algorithm.

What is good enough? The context here is very important when answering that question. For example, if two companies manufacture scales, the first might make scales to weigh highway trucks and the second might make scales to measure gems. The difference in the accuracy of each needed weighing result is very clear. The digital jewelry scale should be able to measure weights even less than 0.1 grams while it is enough for the trucks scale to show the weights in tons.

The other concern we have when solving a problem is the time needed to solve the problem. If the trucks scale mentioned before is going to take half an hour to give me the weight of the truck then I would rather find a different manufacturer which has a product that gives faster solutions. Similarly, when writing a piece of software to solve a problem we care about the accuracy and the time a program takes to find solutions. Therefore, we carefully design the algorithms and try to find creative ways to solve problems.

In computer science, we call a method that sufficiently solves a problem without a guarantee to give a perfect solution a heuristic. These kinds of methods are used to answer the “what is good enough?” question in a reasonable amount of time. If finding the perfect solution takes a year and costs <span>$</span>1,000 then maybe a less accurate but good enough solution that takes a week to find and costs $200 is the perfect solution given all the constraints.

The mathematician [George Polya][GeorgePolya] [1887-1985], who is considered the father of heuristics, described heuristics as “the art of good guessing”. Guessing what might be a good enough solution of the problem using heuristics is considered part of Artificial Intelligence, which is when a computer actually thinks for itself and finds a good solution, rather than mechanically trying all of the possible combinations.

[Douglas Merrill][DouglasMerrill] once said, “All of us is smarter than any of us”. His saying is very evident in the heuristic method designed by Kennedy and Eberhart [1] called Particle Swarm Optimization (PSO). The method is one of the most successful and famous heuristics we use to find approximate “good enough” solutions for very complex and costly problems. PSO is indeed inspired by the fish schooling and birds flocking and depends on the collective intelligence and the high level of collaboration of the swarm. To form a swarm, PSO creates multiple solutions to the problem where each solution (called a particle) represents a fish in the school or a bird in the flock. PSO moves the particles in the problem space by making them follow the one with the best solution, similar to a school or flock where a bird or a fish follow the one closer to the area where the food is. Therefore, PSO is one of the methods that constitutes what is called swarm intelligence systems.

<img style="float: right; width: 60%;" src="{{ site.url }}/assets/images/heuristics/heuristics_takishi_castle.png">

Now, let's take the analogy of [Takeshi's Castle][takishiCastle] - Knock Knock game ([short clip][youtubeClip]) to explain how PSO works. The game works when contenders run through consecutive doors to finally arrive at the end point, and therefore, the game is called “The Wall to Freedom”. In the game, each wall has a set of fake and real doors and a contender needs to find the real door to proceed (The full description of the game can be found on Wikipedia at [this link][knockKnockDesc]). Contenders learn from each other (like a swarm) by following the one who found the real door. And if only one contender was playing the game then multiples of the time is needed to cross all walls since the contender is not learning from anyone without trying by him/herself. Furthermore, since the best solution to the game here is to reach the final point crossing all the 4 walls, a less optimal solution would be to cross 3 or fewer walls. Consequently, the quality of the solution here is judged based on the number of walls crossed, where the higher the number, the better the solution is.

We use PSO to increase the possibility of finding better solutions in less time since in many cases we cannot afford to wait for a long time to find the best solution. The swarm of PSO allows us to investigate multiple solutions to the problem at the same time and judge where to go next in the problem space. Now, let's take a very simple example of a numeric minimization problem.

Suppose that you have the function $ f(x,y)=x-y+7 $, and I asked you to give me the possible values of $ x $ and $ y $ so that to minimize the output value of the function. If the range of the possible values is between $ +100 $ to $ -100 $ for both variables you're obviously going to answer $ -100 $ for $ x $ and $ +100 $ for $ y $ which makes the minimum possible value equal to $ -193 $. However, it is not as straight forward to a computer. Computers execute algorithms in steps and in those steps we change the value of $ x $ and $ y $ then check the quality of the solution, more about that in David J. Malan's talk titled “[What's an algorithm?][whatsanalgo]”.

Imagine that we test every possible solution for this problem, making  $ x=-100 $ and $ y=-100 $ then $ x=-99 $ and $ y=-100 $ until we reach $ x=100 $ and $ y=100 $ and keep track of the quality of the solution each time we vary the values of $ x $ and $ y $. Then, by the end of the algorithm, we would've tried all the possible combinations which equal to $ 200×200=40,000 $ different solutions. The problem I gave you before is a kind of a problem we call a toy (simple) problem in computer science. Now, imagine that we have a more complex problem involving $ 13 $ variables and a range of values between $ -100 $ and $ +100 $. Can you guess how many combinations we have here? I will tell you the answer, we have $ 200^{13} $ combinations, which is around $ 8 $ with $ 29 $ zeros after it.

Accordingly, to find the solution for the example before on the fastest desktop we have now with intel i7 processor the program would finish running after around $ 108 $ billion years (around $ 8 $ times the age of the universe). Which in another way, no thanks! We don't have enough time to wait. Now a good enough solution doesn't sound that bad after all!.

Now, I will explain how PSO work on the toy problem for simplicity. PSO would start by creating, for example, $ 100 $ particles and each particle would get a random value between the given range. For example, Particle-1 numbers would be $ x=5, y=-90 $ which would give an answer of $ 102 $. Particle-2 with the numbers $ x=-90, y=10 $ which would give the answer $ -93 $, and so on. Obviously, the answer of Particle-2 is much better so the idea here is for all the other particles to learn from Particle-2 by assigning random numbers that are close to the ones Particle-2 used before. It means that the particles would learn that it is wiser to use negative values for $ x $ and positives ones for $ y $.

Since PSO is a heuristic method with no guarantees of a perfect solution we can stop running the algorithm at a given point in time and say, OK!, What I found so far is good enough for me. In our previous work [2], however, we used PSO in a combination of other methods and we were able to decrease the running time by about $ 49\% $ of that of the normal method without compromising the quality of the solution. And that was only possible because the swarm allowed us to reflect the idea of good guessing, making PSO the Leonardo da Vinci of computer algorithms.

~~~~
Next, I will be preparing an IPython Notebook to walk you through the implementation of the example above so check out the blog later.
~~~~

[tedTalk]: http://link.hussein.space/howal8515
[GeorgePolya]: http://link.hussein.space/georg3e88
[DouglasMerrill]: http://link.hussein.space/douglfc46
[takishiCastle]: http://link.hussein.space/takese87f
[youtubeClip]: http://link.hussein.space/takes8ed7
[knockKnockDesc]: http://link.hussein.space/listo8bbd
[whatsanalgo]: http://link.hussein.space/whats81c7

## References:

[1] Eberhart, Russ C., and James Kennedy. "A new optimizer using particle swarm theory." In Proceedings of the sixth international symposium on micro machine and human science, vol. 1, pp. 39-43. 1995.

[2] Al-Olimat, H. S., Alam, M., Green, R., & Lee, J. K. (2015). Cloudlet Scheduling with Particle Swarm Optimization. In 2015 Fifth International Conference on Communication Systems and Network Technologies (pp. 991–995). <http://link.hussein.space/ieeex58ac>

[3] Bird Flock. Digital image. Wikimedia.org, n.d. Web. 26 July 2016. <http://link.hussein.space/orgwi96f0>.

[4] Djrhythmdave. "Takeshi's Castle (UK Dub) - Knock Knock." YouTube. YouTube, 15 May 2015. Web. 26 July 2016. <http://link.hussein.space/takes2c9d>.

<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
  });
</script>
