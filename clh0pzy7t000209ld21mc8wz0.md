---
title: "GPT-4 represents progress toward Artificial General Intelligence (AGI) Part - 1"
datePublished: Fri Apr 28 2023 15:40:13 GMT+0000 (Coordinated Universal Time)
cuid: clh0pzy7t000209ld21mc8wz0
slug: gpt-4-represents-progress-toward-artificial-general-intelligence-agi-part-1
canonical: https://daotimes.com/gpt-4-represents-progress-towards-artificial-general-intelligence-part-1/
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683039110125/3fd8f808-8c9e-4099-8015-02586e09e01f.jpeg
tags: ai, daos, gpt-4

---

The advent of artificial intelligence, particularly GPT-4, has created a paradigm shift in the decentralization of power, granting individuals more autonomy and independence.

Through the democratization of knowledge and skill development, people from various backgrounds can now access vast amounts of information, enabling them to make more informed decisions without relying on central authorities. Consequently, AI and GPT-4 serve as catalysts for a more self-reliant and equitable society, where power is dispersed among the people.

In this article you will uncover the potential of GPT-4, OpenAI's innovative large language model, as it reimagines AI capabilities across multiple domains. You will explore its progress towards Artificial General Intelligence (AGI), strengths, and limitations. Witness the future of AI today.

In 1994 a group of 52 psychologists defined intelligence as a very general mental capability that, among other things, involves the ability to reason, plan, solve problems, think abstractly, comprehend complex ideas, learn quickly, and learn from experience ([***Intelligence: Knowns and Unknowns***](https://en.wikipedia.org/wiki/Intelligence:_Knowns_and_Unknowns)). Building an artificial system that exhibits this kind of general intelligence is AI research's long-standing and ambitious goal.

Some recent successes were narrowly focused on well-defined tasks, such as playing chess ([1996](https://en.wikipedia.org/wiki/Deep_Blue_(chess_computer))) or Go ([2016](https://en.wikipedia.org/wiki/AlphaGo)). Artificial General Intelligence (AGI) was popularised in the early 2000s to emphasize the aspiration of moving from "narrow AI," as demonstrated in the focused, real-world applications being developed, to broader notions of intelligence.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682694897138/3f96252b-6075-4a4e-bc0f-66460eda6af5.jpeg align="center")

In the last few years, we have seen a big breakthrough in AI research due to advancements in large language models (LLMs). The main goal of these LLMs is to predict the next word in a partial sentence. The new LLM named [GPT-4](https://openai.com/research/gpt-4) which was developed by [OpenAI](https://openai.com/) exhibits many traits of intelligence, according to the 1994 definition. GPT-4 demonstrates remarkable capabilities in various domains and tasks, including abstraction, comprehension, vision, coding, mathematics, medicine, law, understanding of human motives and emotions, and more.

[**Microsoft**](https://www.microsoft.com/en-in) interacted with an early and non-multimodal version of GPT-4 \[ Note: The final version of GPT-4 was further fine-tuned to improve safety and reduce biases \] using purely natural language queries (prompts). They did several tests including asking it to write a proof of the infinitude of primes in the form of a poem, to draw a unicorn in TiKZ (a language for creating graphics in LATEX), to create a complex animation in Python, and to solve a high-school level mathematical problem. It easily succeeds at all these tasks and produces outputs that are essentially indistinguishable from (or even better than) what humans could produce.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682694947614/023dbc94-84e6-4c22-bd58-70b846fe2cc9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682694956234/5a769feb-0814-4514-ab68-4a33ceab464e.png align="center")

match human abilities (which is how AGI is usually defined). GPT-4 has limitations, even under the 1994 definition of intelligence. It's not entirely clear how it fares on some intelligence criteria such as planning and learning from experience. *Although GPT-4 can learn within a session, it is not continuously updating.* GPT-4 has biases and limitations, such as hallucinations and arithmetic mistakes. However, it has acquired many non-linguistic capabilities (solving LLM failure modes and making progress on common-sense, for instance). GPT-4's intelligence patterns are different from human-like intelligence, but it's a first step towards more generally intelligent systems. GPT-4 has challenged many widely-held assumptions about machine intelligence, and it exhibits behaviors and capabilities whose sources and mechanisms are hard to discern. They believe that GPT-4 is a technological leap that signals a true paradigm shift in computer science and beyond.

![They asked GPT-4 to draw a unicorn in TikZ three times, about once a week for a month while the system was being improved. We can see that the quality of the drawings got better over time.](https://cdn.hashnode.com/res/hashnode/image/upload/v1682694991332/67c2b666-b37f-40ab-ba5c-b1579012636a.png align="center")

We will explore various use cases of GPT-4, covering a range of domains and tasks, and highlighting its strengths and weaknesses.

* GPT-4 excels in natural language processing, generating, and understanding text. It can summarise, translate, and answer a vast range of questions, not only in different languages but also across domains such as medicine, law, accounting, music, and more.
    
* GPT-4 can reason about abstract concepts like coding and math, but there's still much more to explore. They've done some tests, like answering multiple-choice questions in the US Medical Licensing Exam and Multistate Bar Exam, and GPT-4 did pretty well, getting over 70% and 80% accuracy, respectively. Other fields, like medicine and law, could also show GPT-4's reasoning abilities.
    
* They evaluate the model's ability to plan, solve problems, learn quickly, and learn from experience by testing it in various games or simulating a game environment, as well as having it interact with tools. GPT-4's ability to use tools, including itself, will be essential in building real-world applications.
    
* The main point is that GPT-4 performs as well as humans in many tasks but does GPT-4 understands humans as well? They tested if GPT-4 can understand humans and if it can explain itself well. These tasks need common sense. LLMs have struggled with this in the past.
    

Many people may wonder if GPT-4 truly understands concepts, or if it just improved at improvising without truly understanding. After reading the paper, readers may wonder how much more there is to true understanding than improvisation. Is a system that passes software engineering exams not intelligent? The real test of understanding may be producing new knowledge, like proving new math theorems, which LLMs currently can't do.

According to the 1994 definition, Intelligence means being able to reason, plan, solve problems, understand complicated ideas, learn quickly, and learn from experience. GPT-4 has all of these abilities except planning.

| Abilities | Yes / No |
| --- | --- |
| Reason | Yes |
| Plan | *No* |
| Solve problems | Yes |
| Think Abstractly | Yes |
| Comprehend Complex Ideas | Yes |
| Learn Quickly And Learn From Experience | GPT-4 is static and doesn't self-update. |

> ❗ Note: There is no broadly accepted single definition of **intelligence**.

# Microsoft's study of GPT-4's intelligence

To test if a web-trained LLM is intelligent, we usually use standard benchmark datasets to prevent memorization. However, this method may not work for GPT-4 because they lack access to all its data and it has general intelligence beyond narrow AI. GPT-4's best performances are on tasks that have no single solution. To overcome these limitations, they propose a new approach of generating difficult tasks to test and probe GPT-4's consistency, correctness, and limitations. This subjective approach is a useful first step in understanding GPT-4 and developing comprehensive methods for testing AI systems with general intelligence.

In This Article

* Vision
    
* Coding
    
* Mathematical abilities
    
* Interaction with the world
    
* Interaction with humans
    

On Next Article

* Discriminative Capabilities
    
* Limitations of autoregressive architecture highlighted by GPT-4
    
* Societal influences
    
* Directions and Conclusions
    
* GPT-4 has common sense
    

## Vision

Text-to-image models have issues with following complex instructions and placing objects in their correct locations. Recent studies have focused on these models. GPT-4 can create code that produces images, but the results are not visually appealing. To overcome this, we propose using GPT-4 to create a sketch that can be further improved using existing image synthesis models. Our approach, as shown in Figure 2.8, results in images that are both visually appealing and match the given instructions more accurately. This is an example of combining the strengths of GPT-4 and image synthesis models. Further, this approach demonstrates how we can provide GPT-4 with tools to work with, which we explore in more detail in Section.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682695375521/4b451ae5-4968-468c-9596-53160376d84c.png align="center")

## Coding

To measure coding skills, people are given challenges to creating specific functions or algorithms. GPT-4 was tested on HumanEval, a list of 164 coding problems that test different aspects of programming ability. GPT-4 performed better than other similar models, such as text-DaVinci-003 (the basic model for ChatGPT) and other models that were specifically trained on code, like code-DaVinci-002 and CODEGEN-16B.

| Model | GPT-4 | text-DaVinci-003 | Codex(code-DaVinci-002) | CODEGEN-16B |
| --- | --- | --- | --- | --- |
| Accuracy | 82 % | 65% | 39% | 30% |

GPT-4 outperformed previous models in answering questions, but it may have already seen those questions before. To test this, 100 new problems on LeetCode were created as a benchmark. Comparing GPT-4's results to those of other models and humans on the same problems. GPT-4 did much better than other models and almost as well as humans.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682695445768/46e0c656-a178-459e-b92e-45353ecaead4.png align="center")

They asked GPT-4 to create a 3D game in HTML and JavaScript using a high-level description. GPT-4 succeeded, even understanding the concept of "defender avatar is trying to block the enemy." In contrast, ChatGPT could only offer guidance and lacked the ability to create a game from scratch. Developing a 3D game in HTML and JavaScript was challenging and required significant programming experience.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682695776440/a9e5f6e2-f39e-49bd-980f-9857c4e5bea9.png align="center")

## Mathematical abilities

The math abilities of GPT-4, including its understanding of math concepts and problem-solving skills. While GPT-4 outperforms other LLMs, such as Minerva, in math-related tasks, it still falls short of math experts and cannot conduct math research. GPT-4 can answer challenging high-school math problems and discuss advanced math topics, but it may also make errors or provide nonsensical responses, with its math abilities varying depending on the situation.

GPT-4 performance on advanced math topics, demonstrating its capabilities. However, the model may not always be effective on such challenging questions. It is designed for individuals between the ages of 15 and 64 who possess the literacy skills necessary to ask questions. Below is a simplified version of a question from the 2022 International Mathematics Olympiad (IMO).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682695844191/7c2d922c-c5b6-4a74-81a8-9604481aaff4.png align="center")

The question is unique and requires creativity because it is not structured like typical STEM calculus problems. It requires undergraduate-level calculus knowledge to solve, but GPT-4 can solve it correctly.

GPT-4 is knowledgeable about various procedures, such as solving systems of equations, but it often commits errors, such as arithmetic mistakes, rearranging things incorrectly, or using incorrect symbols. To improve the model, it is recommended to allow GPT-4 to use a calculator, if permitted, to verify its calculations or ensure consistency.

## Interaction with the world

To be intelligent, a person must have interactivity skills, which enable them to engage with others and the world. Interactivity is crucial because it facilitates learning, problem-solving, adaptation, and group achievement. People interact to work together, learn, solve problems, and innovate. Being interactive requires understanding complex ideas, quick learning, and learning from experience. Thus, interactivity is a core component of intelligence.

Two ways of interacting: using tools and using natural language. Tools can range from search engines to APIs that help with difficult or impossible tasks. Natural language involves talking with simulated or real-life environments to receive feedback.

Although GPT-4 has limitations such as a lack of knowledge about current events, difficulty with math and symbolic tasks, and inability to execute code, it has performed well in many tasks. However, the model provided inaccurate answers to the first question and performed incorrectly on the second and third questions. ChatGPT also failed to answer the first question and gave incorrect answers to the other questions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682695878148/f1506c8f-1fee-4cd2-80b3-96c9e16af715.png align="center")

GPT-4 can use search engines and APIs to overcome limitations. When a function is called, GPT-4 pauses generation, calls the function, pastes the results into the prompt, and continues generation. GPT-4 uses the tools with minimal instruction and applies the output correctly. ChatGPT does not consistently change its answers after being instructed to use the tools. GPT-4 can list the tools or API functions needed to complete a task.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682695913405/9fe0397b-9637-41b4-8c21-7d8444ca5cbc.png align="center")

GPT-4 can successfully complete complex tasks that require the use of multiple tools. For example, it can understand a task, determine which tools to use, use them in the correct order, and provide the correct response based on their output.

GPT-4 can answers questions by searching the web and using a SUMMARIZE function to identify and summarize important search results. It can provide accurate answers even if the question is based on incorrect information. Unlike earlier LLMs, GPT-4 does not require fine-tuning or demonstration to browse the web.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682696054163/ddbd3635-937a-4f81-bb35-a202073f4072.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682696060878/da19393c-c3f4-423f-a776-be6783e2de08.png align="center")

GPT-4 was tested with an unusual API and found that it didn't adapt to the function. Instead, it called the functions as if they were the usual version, which caused errors. ChatGPT has a similar issue, but it doesn't check for word length. GPT-4 can find and fix its own mistakes, but ChatGPT cannot.

## Interaction with humans

They evaluated the theory of mind abilities of three models, GPT-4, ChatGPT, and text-DaVinci-003, by modifying a classic false-belief test called the Sally-Anne test to ensure that the models were not just memorizing information. GPT-4 performed well on the test, while ChatGPT and text-DaVinci-003 gave less informative answers. They also tested the ability to infer possible intentions in puzzling situations, where GPT-4 performed well. Lastly, they presented some realistic scenarios that require an advanced theory of mind to understand, where GPT-4 performed well while ChatGPT and text-DaVinci-003 struggled.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682696119720/5d01f0c3-f655-44fa-9242-9eea06d2cd8f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682696138733/58d41ffc-a61e-4ef6-84fa-8fdc8efe0b28.png align="center")

# Conclusion

GPT-4, a large language model developed by OpenAI, demonstrates many traits of intelligence according to the 1994 definition. It exhibits remarkable capabilities in various domains and tasks, including abstraction, comprehension, vision, coding, mathematics, medicine, law, understanding of human motives and emotions, and more. Although it has limitations, GPT-4 is a technological leap that signals a true paradigm shift in computer science and beyond, and it represents progress toward Artificial General Intelligence (AGI).

# References

* *S ́ebastien Bubeck, Varun Chandrasekaran, Ronen Eldan, Johannes Gehrke Eric Horvitz Ece Kamar Peter Lee Yin Tat Lee Yuanzhi Li Scott Lundberg Harsha Nori Hamid Palangi Marco Tulio Ribeiro Yi Zhang* \[2023\] **Sparks of Artificial General Intelligence: Early experiments with GPT-4**  [Link](https://arxiv.org/pdf/2303.12712.pdf)
    
* *Sebastien Bubeck* **\[2023\] Sparks of AGI: early experiments with GPT-4** [Link](https://youtu.be/qbIk7-JPB2c)

%[https://youtu.be/qbIk7-JPB2c]