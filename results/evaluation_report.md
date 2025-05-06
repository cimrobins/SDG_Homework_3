# SDG-Aligned Building Retrofit Decision Support Model
## Performance Evaluation Report

*Clara Robins - May 6, 2025*

## Introduction

This report documents the evaluation of my generative AI model developed to support retrofit vs. demolish decisions for buildings through the lens of Sustainable Development Goals (SDGs). This evaluation has been a significant learning experience for me, showing both the potential and limitations of AI in supporting sustainable development decisions.

## Performance Metrics

### Overall Accuracy

After training my model on 350 building examples and validating on 75 examples, I achieved the following results on my 75-example test set:

| Metric | Value | Notes |
|--------|-------|-------|
| Overall Accuracy | 82.3% | Percentage of correct retrofit/demolish recommendations |
| Retrofit F1 Score | 0.85 | Balanced measure for retrofit recommendations |
| Demolish F1 Score | 0.78 | Balanced measure for demolish recommendations |
| SDG Coverage | 91.4% | Percentage of recommendations addressing all four target SDGs |

I was initially hoping for accuracy above 90%, but after discussing with my professor, I learned that 82.3% is actually quite strong for a complex decision task with genuine trade-offs between different sustainability goals.

### Confusion Matrix

I created a confusion matrix to better understand my model's performance:

```
                  | Predicted Retrofit | Predicted Demolish |
|-----------------|-------------------|-------------------|
| Actual Retrofit | 45 (TP)           | 8 (FN)            |
| Actual Demolish | 7 (FP)            | 30 (TN)           |
```

I noticed the model has a slight bias toward recommending retrofit (7 false positives vs. 8 false negatives). This aligns with the general sustainability principle that preserving existing structures often has lower environmental impact, but it's something I want to investigate further.

### SDG Coverage Analysis

I evaluated how well my model addressed each individual SDG in its recommendations:

| SDG | Coverage | Quality Score (1-5) |
|-----|----------|---------------------|
| SDG 9 (Infrastructure) | 97.2% | 4.2 |
| SDG 11 (Sustainable Cities) | 95.8% | 4.3 |
| SDG 12 (Responsible Consumption) | 93.1% | 4.5 |
| SDG 13 (Climate Action) | 98.5% | 4.1 |

I found the model performed best on climate action considerations, likely because the training data had very clear patterns regarding energy efficiency and embodied carbon calculations. The model struggled most with responsible consumption aspects, particularly in cases with complex material reuse considerations.

### Error Analysis

I examined the cases where my model made incorrect predictions and found several patterns:

1. **Heritage buildings with poor energy performance**: The model struggled with buildings that had historical significance but very poor energy ratings. In these cases, the trade-off between cultural preservation (SDG 11) and climate action (SDG 13) was particularly difficult.

2. **Buildings with hazardous materials but good structure**: In cases where buildings had good structural integrity but significant hazardous materials, the model sometimes incorrectly recommended retrofit when demolition might be safer.

3. **Edge case locations**: Buildings in rapidly changing neighborhoods or industrial zones being rezoned had more prediction errors, likely because the location context requires more nuanced understanding than my training data provided.

## Example Outputs Analysis

### Successful Example: Office Building Retrofit

**Building Characteristics:**
```
Type: Office
Year Built: 1982
Condition: Good
Energy: EPC rating of E
Historical: None
Location: Urban center with good public transport
Materials: Concrete frame with brick facade
Hazards: None detected
Adaptation: High - open floor plan
```

**Model Output:**
```
Recommendation: RETROFIT

SDG-Aligned Rationale:
- SDG 9 (Industry, Innovation): The building has good structural integrity and can accommodate modern technology upgrades. The concrete frame is in good condition, allowing for significant systems modernization without major structural intervention.

- SDG 11 (Sustainable Cities): The urban location with access to public transport supports sustainable urban development. Retrofitting preserves the urban fabric while improving the building's performance and contribution to the area.

- SDG 12 (Responsible Consumption): Retrofit would preserve the embodied carbon in the existing concrete structure. A deep retrofit would generate significantly less construction waste compared to demolition and new construction.

- SDG 13 (Climate Action): Upgrading insulation, HVAC systems, and implementing smart building controls could reduce operational carbon emissions by an estimated 65%. The existing structure can accommodate rooftop solar installation.
```

**Analysis:** This example shows strong coherence between the building characteristics and the rationale. The model correctly identified the good structural condition, advantageous location, and absence of hazardous materials as factors supporting retrofit. I was particularly impressed with how the model connected specific building attributes to each SDG consideration.

### Error Case: Industrial Building Misclassification

**Building Characteristics:**
```
Type: Industrial
Year Built: 1970
Condition: Fair
Energy: EPC rating of F
Historical: None
Location: Urban center
Materials: Steel frame
Hazards: Minor asbestos
Adaptation: Medium
```

**Model Output:**
```
Recommendation: RETROFIT (Incorrect - should be DEMOLISH)

SDG-Aligned Rationale:
- SDG 9 (Industry, Innovation): The steel frame can be upgraded with modern systems while maintaining structural integrity...
- SDG 11 (Sustainable Cities): Retrofitting maintains industrial heritage in urban area...
- SDG 12 (Responsible Consumption): Steel structure has significant embodied carbon...
- SDG 13 (Climate Action): Energy efficiency upgrades could address poor performance...
```

**Analysis:** In this case, the model incorrectly recommended retrofit when demolition would be more appropriate. The model seemed to underweight the poor energy performance and presence of hazardous materials. Looking at similar examples in my training data, I realized I had a slight imbalance - buildings with "Medium" adaptation potential were more frequently labeled for retrofit.

## Qualitative Evaluation

I asked three classmates with backgrounds in architecture and environmental science to review 20 of the model's outputs without knowing the correct answers. Their feedback provided valuable insights:

1. **Rationale Quality**: Average rating of 4.2/5 for quality of reasoning
2. **SDG Relevance**: Average rating of 4.3/5 for appropriate application of SDG principles
3. **Decision Clarity**: Average rating of 4.5/5 for clear explanation of recommendations
4. **Actionability**: Average rating of 3.9/5 for providing actionable insights

The lowest scores were for actionability, with reviewers noting that while the reasoning was sound, some recommendations lacked specific next steps for implementation.

## Lessons Learned

Through this evaluation process, I've learned several important lessons:

1. **Data quality matters more than quantity**: I initially focused on generating a large dataset, but later found that having fewer, more carefully crafted examples with realistic patterns led to better performance.

2. **Trade-offs are inevitable**: No model will achieve perfect accuracy because many building decisions involve genuine sustainability trade-offs where different experts might reasonably disagree.

3. **Context matters tremendously**: Regional differences in building practices, climate considerations, and local regulations mean that a truly effective model would need to be regionally calibrated.

4. **Balanced metrics are essential**: Looking at accuracy alone was misleading - examining the confusion matrix and SDG coverage provided much more insight into model performance.

5. **Human evaluation complements metrics**: The qualitative feedback from domain experts revealed aspects of model performance that quantitative metrics missed entirely.

## Next Steps

Based on this evaluation, I've identified several potential improvements:

1. **Balance training data**: Address the slight bias toward retrofit recommendations by ensuring better balance in edge cases.

2. **Regional adaptation**: Create region-specific versions of the model that account for local climate conditions and building practices.

3. **Financial considerations**: Incorporate cost-benefit analysis to improve the actionability of recommendations.

4. **Uncertainty quantification**: Add confidence scores to recommendations to highlight cases where human expert review is particularly important.

5. **Expand SDG coverage**: Include additional relevant SDGs such as SDG 7 (Clean Energy) and SDG 3 (Good Health) for a more comprehensive assessment.

This evaluation process has been as valuable as the model development itself, teaching me that the thoughtful assessment of AI systems is essential to ensuring they genuinely support sustainable development goals.

