from openai import OpenAI

client = OpenAI(api_key="YOUR_API_KEY")

def generate_study_plan(subjects, hours_per_day, exam_days):

    prompt = f"""
    Create a smart study plan.

    Subjects: {subjects}
    Study hours per day: {hours_per_day}
    Days left for exam: {exam_days}

    Generate:
    1. Daily timetable
    2. Subject-wise allocation
    3. Revision schedule
    4. Tips for scoring well
    """

    response = client.chat.completions.create(
        model="gpt-5",
        messages=[
            {"role": "system", "content": "You are an expert study planner."},
            {"role": "user", "content": prompt}
        ]
    )

    return response.choices[0].message.content

# Example
subjects = ["Mathematics", "Physics", "Chemistry", "Programming"]
plan = generate_study_plan(subjects, 6, 30)

print(plan)
