# ai_data_cleaning


Data cleaning experimentation with OpenAI [chat completion API](https://platform.openai.com/docs/guides/text-generation/chat-completions-api) and the [Instructor](https://python.useinstructor.com/) library.<br>
The objective was to experiment how pydantic models can be leveraged to clean data and ensure a structured output.

The material used is a csv file with unstructured fake customer data.
The file consists of a single column where each cell refers to a unique customer. 

In each cell, the following information can be found:
- first name
- last name
- current age
- city
- account type (premium or non-premium)

The data is intentionnally diverse in terms of structure (e.g. " current_age:"24" " for the first customer and "36Y.O" for the last)



