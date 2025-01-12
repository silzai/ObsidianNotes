```python
from pptx import Presentation

# Create a PowerPoint presentation
presentation = Presentation()

# Helper function to add a slide with title and content
def add_slide(presentation, title, content):
    slide = presentation.slides.add_slide(presentation.slide_layouts[1])
    slide.shapes.title.text = title
    textbox = slide.placeholders[1]
    textbox.text = content

# Slide 1: Title Slide
slide = presentation.slides.add_slide(presentation.slide_layouts[0])
slide.shapes.title.text = "Diabetes: A Comprehensive Overview"
subtitle = slide.placeholders[1]
subtitle.text = "Understanding the causes, types, management, and impact of diabetes."

# Slide 2: Introduction
add_slide(
    presentation,
    "Introduction",
    """Definition:
Diabetes is a chronic medical condition where the body fails to regulate blood glucose levels effectively.

Key Statistics:
- Over 422 million people worldwide have diabetes (WHO, 2021).
- Diabetes caused 1.5 million deaths in 2019.
- Prevalence is increasing, especially in low- and middle-income countries.""",
)

# Slide 3: How Diabetes Works
add_slide(
    presentation,
    "How Diabetes Works",
    """Normal Blood Glucose Regulation:
- Glucose is a primary energy source.
- Insulin, produced by the pancreas, allows cells to absorb glucose.
- Excess glucose is stored in the liver.

In Diabetes:
- Insufficient insulin is produced (Type 1), or cells become resistant to insulin (Type 2).
- Results in hyperglycemia (high blood sugar).""",
)

# Slide 4: Types of Diabetes
add_slide(
    presentation,
    "Types of Diabetes",
    """1. Type 1 Diabetes:
- Autoimmune condition; immune system attacks insulin-producing beta cells.
- Usually diagnosed in children and young adults.
- Treatment: Insulin therapy.

2. Type 2 Diabetes:
- Insulin resistance and relative insulin deficiency.
- Linked to obesity and inactivity.
- Preventable and manageable through lifestyle changes.

3. Gestational Diabetes:
- Occurs during pregnancy; increases risk of Type 2 diabetes later.

4. Other Types:
- MODY (Maturity Onset Diabetes of the Young).
- Secondary diabetes (due to medications or conditions).""",
)

# Slide 5: Risk Factors
add_slide(
    presentation,
    "Risk Factors",
    """Type 1 Diabetes:
- Genetic predisposition.
- Environmental triggers (e.g., viral infections).

Type 2 Diabetes:
- Obesity and physical inactivity.
- Family history of diabetes.
- Unhealthy diet and stress.
- Age (higher risk in older adults).

Gestational Diabetes:
- History of macrosomic baby (>9 pounds).
- Hormonal changes during pregnancy.""",
)

# Slide 6: Symptoms
add_slide(
    presentation,
    "Symptoms",
    """- Increased thirst and urination.
- Unexplained weight loss.
- Fatigue and weakness.
- Blurred vision.
- Slow healing of wounds.
- Frequent infections.""",
)

# Slide 7: Complications
add_slide(
    presentation,
    "Complications",
    """Acute Complications:
- Diabetic ketoacidosis (DKA).
- Hyperosmolar hyperglycemic state (HHS).

Chronic Complications:
- Cardiovascular diseases.
- Neuropathy (nerve damage).
- Retinopathy (vision problems).
- Nephropathy (kidney damage).
- Limb amputations.""",
)

# Slide 8: Diagnosis
add_slide(
    presentation,
    "Diagnosis",
    """Blood Tests:
- Fasting Plasma Glucose (FPG): ≥126 mg/dL indicates diabetes.
- HbA1c Test: ≥6.5% indicates diabetes.
- Oral Glucose Tolerance Test (OGTT).

Monitoring:
- Continuous Glucose Monitors (CGMs) and fingerstick blood tests.""",
)

# Slide 9: Management and Treatment
add_slide(
    presentation,
    "Management and Treatment",
    """Lifestyle Modifications:
- Balanced diet (low glycemic index foods, high fiber).
- Regular physical activity (150 minutes/week).
- Weight management.

Medications:
- Type 1: Insulin therapy.
- Type 2: Metformin, SGLT2 inhibitors, GLP-1 receptor agonists.

Emerging Therapies:
- Artificial pancreas systems.
- Stem cell research.""",
)

# Slide 10: Prevention
add_slide(
    presentation,
    "Prevention",
    """Type 1 Diabetes:
- Not preventable currently.

Type 2 Diabetes:
- Maintain healthy body weight.
- Regular physical activity.
- Avoid excessive sugar and processed foods.

Community Efforts:
- Public awareness campaigns.
- Screening programs in high-risk populations.""",
)

# Slide 11: Impact of Diabetes
add_slide(
    presentation,
    "Impact of Diabetes",
    """Health Systems:
- High healthcare costs for managing complications.

Economic Impact:
- Loss of productivity and increased absenteeism.

Social Impact:
- Reduced quality of life for patients and caregivers.""",
)

# Slide 12: Global Perspective
add_slide(
    presentation,
    "Global Perspective",
    """Geographical Prevalence:
- High prevalence in South Asia, the Middle East, and the Americas.

Organizations Fighting Diabetes:
- International Diabetes Federation (IDF).
- World Health Organization (WHO).
- National Diabetes Prevention Programs (e.g., CDC in the U.S.).""",
)

# Slide 13: Case Study
add_slide(
    presentation,
    "Case Study",
    """Scenario:
A patient with Type 2 diabetes and obesity.

Approach:
- Initial treatment: Lifestyle changes and Metformin.
- Monitoring: CGM to track glucose levels.

Progress:
- HbA1c dropped from 8.5% to 6.5% after 6 months.

Key Takeaway:
- Multidisciplinary care improves outcomes.""",
)

# Slide 14: Future Directions
add_slide(
    presentation,
    "Future Directions",
    """Technological Advances:
- AI-powered glucose monitors and apps.
- Improved insulin delivery systems.

Research Areas:
- Genetic studies for Type 1 prevention.
- New drugs targeting insulin resistance.
- Community-based preventive healthcare models.""",
)

# Slide 15: Conclusion
add_slide(
    presentation,
    "Conclusion",
    """Summary:
- Diabetes is a manageable but serious condition with rising prevalence.
- Early detection, prevention, and effective management reduce complications.

Call to Action:
- Promote awareness and lifestyle changes.
- Advocate for accessible healthcare and support systems.""",
)

# Save the presentation
file_path = "/mnt/data/Diabetes_Presentation.pptx"
presentation.save(file_path)

file_path

```