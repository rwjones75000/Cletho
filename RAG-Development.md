# 🧠 RAG Prompt Augmentation Cheat Sheet

This cheat sheet walks through the 5 essential steps for turning structured data into augmented prompts for Large Language Models (LLMs), forming the foundation of Retrieval-Augmented Generation (RAG).

---

## Step 1: Start with Structured Data

You’ll typically have a list of dictionaries — for example, from a JSON file or database:

```python
house_data = [
    {
        "address": "123 Maple Street",
        "city": "Springfield",
        "bedrooms": 3,
        "price": 230000
    },
    {
        "address": "456 Elm Avenue",
        "city": "Shelbyville",
        "bedrooms": 4,
        "price": 320000
    }
]
```

## Step 2: Format Each Item into Readable Text
Use f-strings to convert each dictionary into a natural-language sentence. This makes the structured data human- and model-readable. It's similar to rendering chunks in a RAG system.

```python
def format_house(house):
    return (
        f"{house['address']}, {house['city']} — "
        f"{house['bedrooms']} bedrooms, ${house['price']}"
    )
```

## Step 3: Combine All Items into One Context Block
Create a function to merge all formatted items into a single string, separated by line breaks. This block will serve as the "retrieved context" in your prompt.

```python   
def house_info_layout(houses):
    return "\n".join([format_house(h) for h in houses])
```

## Step 4: Build the Full Augmented Prompt
Now, assemble the instruction, context, and user query into a single prompt that can be passed to the LLM. This is the augmented prompt: it provides the model with structured information and a specific query.

```python
def generate_prompt(query, houses):
    layout = house_info_layout(houses)
    return f"""
Use the following house listings to answer the question:

{layout}

Question: {query}
"""
```

## Step 5: Send It to the LLM
Finally, send the full prompt to the LLM using your wrapper function (e.g. `generate_with_single_input()`):

```python   
prompt = generate_prompt("Which house is the most expensive?", house_data)

response = generate_with_single_input(prompt=prompt)
print(response["content"])
```

---   

## Summary Pattern
You can adapt this pattern to other use cases by renaming the functions and changing the structure of the data. Here’s a reusable template:

```python
def format_chunk(item): ...
def layout_chunks(data): ...
def generate_augmented_prompt(query, data, instruction="Use the following context to answer the question:"): ...
```
