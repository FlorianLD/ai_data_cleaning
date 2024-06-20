# About

Data cleaning experiment with OpenAI [chat completion API](https://platform.openai.com/docs/guides/text-generation/chat-completions-api) and the [Instructor](https://python.useinstructor.com/) library.<br>
The objective was to see how pydantic models can be leveraged to clean data and ensure a structured output consistently.<br>
See notebook [here](https://github.com/FlorianLD/ai_data_cleaning/blob/main/ai_data_cleaning.ipynb).

The material used is a csv file with unstructured fake customer data.
The file consists of a single column where each cell refers to a unique customer. 

In each cell, the following information can be found, in a random order:
- first name
- last name
- current age
- city
- account type (premium or non-premium)

The data structure is intentionnally diverse for a more challenging test case.

![Material](/material.png)

By using models and passing them in the `response_model` parameter of the function, the following output can be obtained

![Final](/final_output.png)

Model used:
```
class Premium(Enum):
    """Defines the type of account of the customer, either premium or non-premium"""
    PREMIUM = 1
    NON_PREMIUM = 0

class Customer(BaseModel):
    """Represents a customer, including their first name, last name, age, city, and type of account"""
    first_name: str = Field(..., description="The first name of the customer")
    last_name: str = Field(..., description="The last name of the customer")
    age: int = Field(..., description="The age of the customer")
    city: str = Field(... , description="The city where the customer lives")
    premium: Premium = Field(..., description="Type of account, either premium or non-premium")

class CustomerList(BaseModel):
    """A list of customers"""
    customers: List[Customer] = Field(..., description="A list of customers")
```
