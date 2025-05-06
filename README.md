# Homework 3: AI for Sustainable Building Decisions

## My Learning Journey in AI and Sustainable Development 

Welcome to my homework project for AI for Sustainable Development! As a student exploring how AI can help solve real-world sustainability challenges, I've created a decision support tool that helps building professionals determine whether to retrofit or demolish existing buildings, with recommendations aligned to the UN Sustainable Development Goals (SDGs).

![SDG Goals](https://sdgs.un.org/sites/default/files/2020-07/SDGs-banner.jpg)

## Repository Structure

This repository contains my entire learning process and project deliverables:

- **[`/notebooks/model_training.ipynb`](notebooks/model_training.ipynb)**: Jupyter notebook with my model development process
- **[`/results/evaluation_report.md`](results/evaluation_report.md)**: Detailed analysis of my model's performance
- **[`/docs/sdg_discussion.md`](docs/sdg_discussion.md)**: My reflection on AI's role in advancing SDGs

## The Problem I'm Addressing

When I first started this project, I was surprised to learn that buildings account for approximately 40% of global carbon emissions! The decision between retrofitting versus demolishing buildings has significant sustainability implications, but these decisions are often made without a comprehensive framework.

I realized AI could help by providing recommendations that balance multiple sustainability dimensions across different SDGs:

- **SDG 9**: Industry, Innovation & Infrastructure
- **SDG 11**: Sustainable Cities & Communities
- **SDG 12**: Responsible Consumption & Production
- **SDG 13**: Climate Action

## My Learning Process

### What I Did First

I started by researching sustainability principles in the built environment and looking for existing datasets on retrofit/demolish decisions. To my surprise, I couldn't find comprehensive data that included SDG-aligned rationales. I realized I would need to create this data myself based on building science principles.

This was harder than I expected! I had to learn about building science concepts like embodied carbon, adaptation potential, and energy performance certifications. I also needed to understand how these factors connect to specific SDGs.

### Creating a Prototype

My first attempt at generating data was too random and didn't reflect real-world patterns. I realized I needed a more systematic approach with rules that reflected actual retrofit/demolish decision factors:

```python
# My first attempt at creating a rule-based system
def determine_recommendation(building):
    retrofit_points = 0
    demolish_points = 0
    
    # Age and historical significance
    if building["year_built"] < 1950:
        if building["historical_significance"] in ["National significance", "Local significance"]:
            retrofit_points += 2  # Strong preference for historical preservation
        else:
            demolish_points += 1  # Slight preference for replacement if very old
            
    # Building condition...
    # [Additional rules I developed]
```

Through iterative improvement, I created a dataset of 500 building examples with retrofit/demolish recommendations and SDG-aligned rationales.

### Model Development Challenges

This was my first time working with a generative AI model for a real application. I chose GPT-2 for my base model, but quickly ran into challenges:

1. **Prompt Engineering**: Getting the model to consistently address all four SDGs required careful prompt design
2. **Balancing Factors**: The model would sometimes overemphasize one sustainability factor (like energy) while overlooking others (like material waste)
3. **Maintaining Technical Accuracy**: Ensuring building science concepts were correctly applied in generated text

I documented my process in the [model training notebook](notebooks/model_training.ipynb), including my experiments and iterations.

### What I Learned About Evaluation

My most valuable lesson was the importance of comprehensive evaluation. I initially focused solely on decision accuracy (82.3%), but realized this metric alone wasn't enough. I needed to evaluate:

- How well each SDG was covered (ranging from 93.1% to 98.5%)
- The quality and specificity of the generated rationales
- Pattern analysis of error cases (which building types caused confusion)

The [evaluation report](results/evaluation_report.md) documents my findings and analysis.

## Key Results

After several iterations, my model achieved:
- 82.3% accuracy on retrofit/demolish decisions
- 91.4% coverage of all four SDGs in recommendations
- Comprehensive explanations connecting building characteristics to specific SDG considerations

More importantly, I learned how to operationalize sustainability principles into AI applications, balancing multiple competing factors and creating transparent, explainable recommendations.

## Reflection on AI and SDGs

This project transformed my understanding of how AI can support sustainable development. In my [SDG discussion](docs/sdg_discussion.md), I reflect on AI's potential to operationalize abstract SDG principles and the challenges of balancing competing sustainability objectives.

The most valuable insight for me was seeing how AI can help scale sustainable decision-making while making the reasoning process more transparent. By systematically addressing multiple SDGs in each recommendation, the model forces consideration of sustainability dimensions that might otherwise be overlooked.

## Next Steps

If I continue this project, I'd like to:
1. Include financial considerations to improve actionability
2. Create region-specific variants for different climates and building codes
3. Add uncertainty estimates to highlight when human judgment is most needed

I welcome any feedback or questions about my learning process and project results!

