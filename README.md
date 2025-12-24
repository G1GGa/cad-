import google.generativeai as genai

# API key
genai.configure(api_key="YOUR_GOOGLE_API_KEY")
model = genai.GenerativeModel("gemini-1.5-flash")

# 3D Object example (Easy representation)
design = {
    "object": "Drone frame",
    "dimensions": {"length": 1.2, "width": 0.8, "height": 0.3},  # meters
    "load": 15,  # kg
    "temperature_range": [-20, 80],  # Celsius
}

# Material library
materials = [
    {"name": "Titanium Alloy", "density": 4500, "strength": 900, "thermal_conductivity": 15},
    {"name": "Carbon Fiber", "density": 1600, "strength": 700, "thermal_conductivity": 10},
    {"name": "Aluminum", "density": 2700, "strength": 300, "thermal_conductivity": 205},
]

# AI prompt
prompt = f"""
You are an AI assistant for 3D engineering design.
The user has the following 3D object design: {design}
Available materials: {materials}
Recommend the most suitable material(s) for this design and explain the impact on structure, weight, and heat resistance.
"""

response = model.generate_content(prompt)
print("AI Recommendation:\n", response.text)
