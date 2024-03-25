# PersonalChef-AI-Powered-Recipe-Generator
PersonalChef uses ML and generative AI to create personalized recipes based on users' dietary preferences, allergies, and available ingredients, making cooking easy and enjoyable.
import random

# Sample data to simulate AI model's knowledge base
recipes_data = {
    'vegan': [
        {'name': 'Vegan Lasagna', 'ingredients': ['lasagna noodles', 'tomato sauce', 'vegan cheese', 'spinach']},
        {'name': 'Quinoa Salad', 'ingredients': ['quinoa', 'cucumbers', 'tomatoes', 'avocado', 'lemon juice']}
    ],
    'gluten-free': [
        {'name': 'Stuffed Peppers', 'ingredients': ['bell peppers', 'ground turkey', 'rice', 'tomato sauce']},
        {'name': 'Almond Flour Pancakes', 'ingredients': ['almond flour', 'eggs', 'almond milk', 'maple syrup']}
    ]
    # Additional categories can be added here
}

def generate_recipe(dietary_preference, allergies, available_ingredients):
    potential_recipes = recipes_data.get(dietary_preference, [])
    
    # Filter out recipes containing any allergens
    safe_recipes = [recipe for recipe in potential_recipes if not any(allergen in recipe['ingredients'] for allergen in allergies)]
    
    # Filter based on available ingredients
    matched_recipes = [recipe for recipe in safe_recipes if all(ingredient in available_ingredients for ingredient in recipe['ingredients'])]
    
    if matched_recipes:
        return random.choice(matched_recipes)
    else:
        return "No matching recipes found. Try adjusting your filters."

# Example usage
user_dietary_preference = 'vegan'
user_allergies = ['nuts']
user_available_ingredients = ['lasagna noodles', 'tomato sauce', 'vegan cheese', 'spinach']

recipe = generate_recipe(user_dietary_preference, user_allergies, user_available_ingredients)
print(f"Recommended Recipe: {recipe['name']}")
print("Ingredients needed: " + ", ".join(recipe['ingredients']))
