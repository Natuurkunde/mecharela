# Preface

In this book, you'll find an introduction into the physics of mechanical systems. The material in the book has evolved from lecture notes on courses in introductory physics I have taught at TU Delft since 2012. In most cases, not all of the material covered in the book were discussed in the lectures. In particular sections indicated with a star are extra material, for those interested in learning more. The chapters also do not necessarily be taught or read in the order I have presented them. For example, many of the concepts of {numref}`ch:oscillations` can be understood based on the material covered in {numref}`ch:mechanicsintroduction`-{numref}`ch:energy`. There are thus multiple paths you can take, and I encourage you to look ahead sometimes to see how what is yet to come ties in with what is discussed at a given point in the book. If you need refresher on some of the mathematical techniques, {numref}`app:math` contains some useful background maths. Throughout, I've tried to alternate theory with worked examples, to give you an idea about what you can actually do with the theory just developed.

Roughly the first part of this book ({numref}`ch:mechanicsintroduction`-{numref}`ch:oscillations` and {numref}`ch:waves`) also appear in [*Mechanics and Relativity](https://textbooks.open.tudelft.nl/textbooks/catalog/book/14)* (TU Delft Open, 2018). Where applicable, I've made corrections and occasional small extensions, which will also appear in an updated version of *Mechanics and Relativity*, together with the extra {numref}`ch:Lagrangianmechanics` on Lagrangian mechanics. In turn, the new chapters on continuum materials connect to the MSc-level book I'm currently writing on soft matter physics.

Students often ask me how to best study for an exam. Here are three key steps to successfully completing any course in physics (or probably any field of study), which for maximum effect, are best taken throughout the course:
- **Prepare**: Read the assigned sections before the class, look at the problems before the tutorial.
- **Participate**: Attend class, join in any quizzes / problem sessions offered, ask questions whenever you don't understand.
- **Practice**: Make all problems, both in practice sessions and in homework. Try yourself before an exam by doing last year's exam. Resist the urge to look up the answers.


Like learning maths, or playing the piano, learning to do physics takes practice. There are no quick fixes. This especially goes for doing problems: looking up the solution is not equivalent to finding the solution yourself! Of course I understand you want to check your answer, which is fine - but do not look for the solution method, as you'll only fool yourself into thinking you understand. You only really understand if you've found the solution yourself, and can explain to someone else why it gives the right answer. The numerical value of that answer is of little interest - it's the method that counts! In fact, you should avoid putting in numbers altogether (only do so in the final step if a number is asked for), as a symbolic answer will tell you much more: whether the dimensions match, whether limit cases make sense, and whether the answer itself can be understood from scaling.

Now if you find you do not understand something - no worries, that's what teachers are for! By all means, ask. Of course, you can also ask another student - you'd actually be doing them a favor, as by explaining it to you, they get better understanding themselves. Moreover, whenever you find in class or during a problem session you do not understand, there are likely others who don't understand either - and you'd be helping the teachers by asking a question.

My goal, as a teacher, is to help you get a feeling for the basic principles that govern the physical world both at the everyday level and in the exotic world of relativity. However, I cannot do this without your active participation, nor without your feedback in the form of questions. I expect a lot from you, and you can expect a lot from me too. In particular, I will keep working on improving this text, and so any questions or comments you may have are very welcome - I love interaction! So please don't be shy, but by all means let me know what you think of the book, and whether it helped you understand physics better.




## How to tackle a problem: The IDEA method
Americans love acronyms (apparently these are a good way of getting things stuck in people's head), so they call the three key steps in the previous section the 'PPP' method, and have likewise come up with a nice one for a very useful way to tackle a physics problem: Identify, Develop, Evaluate, and Assess, or IDEA. This method is especially helpful for the often feared first step: how do you translate a problem into a set of equations that you can solve? The first thing to do is usually quite simple: identify which kind of problem you're dealing with. You may be asked about a minimal force to keep things stable, the amount of work necessary to perform a certain task, or the velocities of two billiard balls after a collision. We'll cover such cases in the worked examples and problems, where the identification step has already been taken (it's the topic under discussion) - but in the end you should be able to classify the problem yourself. There is a huge bonus to that classification, as it immediately tells you which laws apply - see the mind-map in {numref}`fig:mechanicsproblems`. I encourage you to make a similar scheme for both the mechanics and the relativity part of the course for yourself - it's a great way of summarizing the material.

```{figure} images/mechanics/mechanicsproblems.pdf
:name: fig:mechanicsproblems
(Simplified) schematic overview of a classification of mechanics problems, with the relevant laws indicated.
```


Once you have identified the type of problem, you can go ahead and develop it. First, make a sketch of the situation, and collect all necessary information, which you can put in the sketch (for example drawing all relevant forces in a free body diagram, see {numref}`sec:multipleforces`). Second, write down the relevant laws in the form that applies to the case at hand. In some cases, this is simply one equation, while in others, you may end up with a system of equations - so the evaluation step can be quite complicated. In either case, you will find your sketch helpful in identifying all relevant laws, and thus equations. Now that you have developed the problem, the next step is to evaluate it, i.e., solve the equations for the quantity asked for in the problem. To simplify the evaluation, it is often easier not to plug in any numbers - except of course when the numbers are very simple or hugely simplify your system (such as crossing out terms that are zero). Exactly because the evaluation step can be tricky, it is always a good idea to assess your answer. Does the number you get in the end make sense? Does your answer have the right dimensions (see {numref}`sec:dimanalysis`)? Does it behave in the way you'd expect if you take the value of one of the parameters to zero, or infinity? We'll practice with this explicitly in the problems, and I encourage you to keep on doing it - it will save you from some embarrassing mishaps in the end.




## Heros of physics
All of the material discussed in this book is classical physics, mostly developed prior to the 20th century. Of course, physics, or rather the physicists, have not been idle since, and many new physical principles have been discovered since, but the ones discussed here remain valid. In fact, they remain extremely useful, not only in many applications (including engineering, architecture, and spaceflight), but also in ongoing physics research. For example, in my own field of biophysics, a key process is cell division, in which the pulling apart of the two copies of the DNA is a crucial step. Forces generated by small molecular motors are central players in that process, and they obey Newton's laws just like the (probably apocryphal) apple falling on Newton's head did.

In doing research or applications today, we are, in Newton's words, standing on the shoulders of the giants who came before us. I've added the stories of some of these giants throughout the book, though with a somewhat double feeling. On the one hand, these giants definitely deserve the credit for the work they've done, and some of them were examples of dedication and diligence. On the other hand, the list of people can never be inclusive (there are many others who contributed as well), and the list has the distinct disadvantage of being very un-diverse: these people are all white, almost all men, and almost all from Europe. The reason for this limited variety of course is that up until the early 20th century, only white European men had any chance of being in a position privileged enough to be able to dedicate a significant amount of their time to research. That is not to say that they never met trouble, but that others simply never got the chance. Fortunately, although we're still far from a perfect world, things on that front have improved tremendously, and so please take these people for what they were: dedicated, curious people who were interested in finding out how the world works. I hope the same goes for you, and that with this book, I can help you a bit on the path towards becoming a physicist yourself.


\begin{flushright}
{\makeatletter\itshape
    \@firstname\ \@lastname \\
    Delft, September 2023
\makeatother}
\end{flushright}

