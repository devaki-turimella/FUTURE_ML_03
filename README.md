Resume Screening and Ranking System

What this project does
Hiring teams get hundreds of resumes for one job, and checking each one manually takes a lot of time. This project automatically:
1. Cleans resume text (lowercase, remove symbols/numbers, remove stopwords)
2. Extracts skills from resumes using keyword based NLP matching
3. Takes a Job Description (JD) and extracts the required skills from it too
4. Compares every resume with the JD using TF-IDF + Cosine Similarity
5. Ranks all candidates from best match to worst match
6. Shows missing skills (skill gap) for every candidate compared to the JD
7. Saves a bar chart and a final ranked csv file as output

Dataset used
Kaggle "Resume Dataset" by snehaanbhawal
(`Resume.csv` file with columns: ID, Resume_str, Resume_html, Category)
Link: https://www.kaggle.com/datasets/snehaanbhawal/resume-dataset

The dataset already gives resume text extracted from the original PDFs,
so we directly used the `Resume_str` column instead of doing PDF parsing again.

How the scoring works :
- convertig resume text and job description text into numbers using TF-IDF (this basically gives importance to words that are unique/relevant in a document)
- Then check how "close" each resume vector is to the job description vector using cosine similarity. Closer = higher match score (in %).
- Candidates with the highest score are the ones whose resume text is most similar to what the job description is asking for.
  
Why some candidates rank higher
- Their resume text contains more of the same important words/skills that are present in the job description.
- Resumes which don't mention those specific skills get a lower score, even if they are good resumes overall, because TF-IDF only looks at word overlap, not actual experience/quality.

Skill list used


A simple custom skill list (`SKILL_LIST` in the code) is used for keyword based skill extraction. This is a basic NLP technique. It can easily be extended to
add more skills depending on the job role, or upgraded to spaCy Named Entity Recognition for more advanced extraction.
Python, Pandas, Scikit-learn (TF-IDF + Cosine Similarity), Matplotlib

Author - by Devaki
