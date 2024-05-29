# AI Definition

Although only two main studies appear to have been conducted on the topic of API Documentation Smells related to the presentation of the content, this topic has most certainly been discussed in other circles.

With the current advancements of AI technologies, and specifically Large Language Models, Ai services like ChatGPT or Gemini are capable of aggregating information on these topics and provide more extended definitions. Although not perfect, these definitions seem to correlate with the study-defined ones, and can help providing a more general idea of what the Excess Structural Information Smell entails.

## ChatGPT

When asked about Excess Structural Information Smell, ChatGPT defined it as such:

> * **Description**: This smell arises when the API documentation focuses too much on the structure of the API itself, such as its endpoints, methods, or classes, rather than providing meaningful explanations of how to use those elements effectively. Excessive structural information without sufficient contextual guidance can confuse developers and hinder their understanding.
> * **Impact**: Developers may struggle to grasp the purpose and usage of the API components, leading to inefficiencies in implementation and increased learning curves. Without clear explanations and examples, developers may resort to trial and error, resulting in suboptimal use of the API.

It also recommended the following mitigation strategies:

> To mitigate the Excess Structural Information Smell, documentation should focus on:
>
> * **High-Level Overviews**: Providing a high-level overview of the API's functionality and how it can be used to accomplish specific tasks.
> * **Task-Oriented Descriptions**: Focusing on what the API does and how to use it, rather than how it is implemented internally.
> * **Relevant Examples**: Including practical examples and use cases that show how to interact with the API.
> * **Clear Separation**: Clearly separating user-relevant information from internal implementation details, possibly placing the latter in separate sections or appendices if they need to be documented at all.

## Gemini

When asked the same task of definition Excess Structural Information Smell, Gemini gave a similar definition. Interestingly though, it defined it as a subtype of Bloated Documentation Smell, smell with which, according to the study by Khan et al., it has the highest correlation.

> **Excess Structural Information Smell:** This is a specific type of Bloated Documentation Smell. It focuses on documentation that includes too many structural details rather than focusing on the functionality itself. Imagine a JavaDoc for a simple class that lists every single inherited method from the Object class – that would be Excess Structural Information Smell.

It also recommended the following mitigation strategies:

> * **Focus on Functionality:** Remember, the documentation exists to explain how to use the software, not every intricate detail of the code itself. Prioritize explaining what the code does for the user, rather than how it achieves it on a technical level.
> * **Use Targeted Examples:** Instead of listing every inherited method, focus on showcasing the functionality through relevant examples. Demonstrate how a specific class or method is used in a practical context.
> * **Leverage Automatic Inclusions:** Many IDEs and documentation tools can automatically include basic structural information like inherited methods. This frees you from manually listing them, allowing you to focus on explaining the functionality specific to your code.
> * **Prioritize User Needs:** Think about your target audience. Are they developers needing deep technical details, or end-users just trying to understand how to use the software effectively? Tailor the level of structural information to their needs.
> * **Link to References:** If there's a need to reference specific aspects of the underlying code structure, consider linking to a separate reference document. This keeps the main documentation focused on functionality while providing more detailed information for those who need it.
