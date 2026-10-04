# What was build and why

- **Student Risk Engine** - Calculated a risk score based on weather students are declining or improving, practice completion, quiz performance, number of notes facilitator, to identify students most likely to fall behind before the next quiz.
- **Facilitator Action Queue** - Converted risk scores into a ranked daily intervention list so facilitators know exactly who to help first.
- **Recommendation Layer** - Generated the highest-impact next action and root cause for each student to reduce facilitator decision-making overhead.
- **AI Intelligence Layer** - Used LLMs to extract signals from facilitator notes and add risk score from 0.1 to 2, explain risk scores, and identify recurring patterns across struggling students.


# **What’s found and fixed the data**

- **Facilitator notes and behavioral metrics were internally consistent.** Notes in `facilitator_notes.csv` frequently aligned with attendance and engagement patterns in `student_daily_metrics.csv` through the shared `student_id`. For example, a note for S190 describing attendance dropping from 90 to 20 minutes matched the corresponding attendance record, making the two datasets suitable for joint analysis despite the synthetic nature of the data.
- while In `student_metadata.csv`, students are assigned to facilitators in contiguous ID ranges (e.g., `facilitator1@noon.com` manages S001–S020, `facilitator2@noon.com` manages S021–S040) which doesn’t align with both `facilitator_notes.csv` and `student_daily_metrics.csv` .
- The busiest facilitator handled 4× more students than the least busy facilitator & Three facilitators account for 40% of all intervention activity indicating there’s no workload management system
- **A significant number of students had no documented facilitator interaction despite having measurable engagement data.** This created an "invisibility" problem where students could decline for days without appearing in any facilitator workflow.


## Getting Started

Follow these steps to set up and run the application locally:

### 1. Clone the Repository
Clone the project directory to your local machine (or use the existing directory):
```bash
git clone https://github.com/amarelriany/case-study-noon-academy.git
cd Case-study-noon-academy
```

### 2. Install Dependencies
Install all the required Python packages:
```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables
Create a `.env` file in the root of the project directory and specify your API key:
```env
GPT_API_KEY=your_openai_api_key_here
```

### 6. Start the Web Server
Launch the Flask development server:
```bash
python app.py
```