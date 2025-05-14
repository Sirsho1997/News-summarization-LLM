#  News-summarization-LLM

This project demonstrates how to apply full-fine-tune and PEFT to FLAN-T5 to generate summaries of Indian news articles. This project explores text preprocessing, model inference, and evaluation using real-world Indian journalism data.

## Requirements

Install the necessary Python packages:

```bash
pip install transformers datasets nltk rouge-score pandas scikit-learn
```


## Dataset Description

The **News Article Dataset** [News Article Dataset](https://www.kaggle.com/datasets/teja098/news-article) is a curated collection of **112 news articles** sourced from leading Indian newspapers, such as:

- *The Hindu*
- *Hindustan Times*
- *Indian Express*
- ...and others.

Each data record includes:
- `Newspaper Name`: Source of the article  
- `Published Date`: Date of publication  
- `URL`: Link to the original article  
- `Headline`: Article title  
- `Content`: Full article text  
- `Human Summary`: Expert-written summary  
- `Category`: News classification (e.g., Science and Technology, Business, Environment)

🔍 **Note**: For this summarization task, **only the `Content` and `Human Summary` columns are used**.

## Sample Output

Input prompt:
```
Summarize the following news.

Water Minister and Delhi Jal Board (DJB) chairman Satyendar Jain on Saturday visited Rohini Lake to review the progress of various units being constructed in line with the Delhi government’s objective of transforming the Capital into “a city of lakes”.

The government plans to develop Rohini as an “abode of lakes and recreation” within 8 months.

A project revolving around the revival of lakes and water bodies in Delhi is on the AAP government’s list of priorities, the government stated, adding that it soug
```
Human Summary:
```
Delhi Water Minister Satyendar Jain visited Rohini Lake to assess the progress of the Delhi government's "City of Lakes" project, aimed at reviving lakes and water bodies across the city. The government plans to transform Rohini into an "abode of lakes and recreation" within 8 months. The project involves reviving eight lakes to recharge 68 MLD of treated water from a sewage treatment plant (STP). The broader initiative focuses on creating reservoirs to reduce urban flooding. Rohini Lake, part of a 100-acre complex, will receive treated wastewater and is set to be completed within eight months.
```
Model generated - zero shot:
```
The Delhi government has announced plans to build a lake in the capital, Rohini, to help revive the city’s lakes.
```

## Evaluation

The quality of the generated summaries is evaluated using:

ROUGE-1: Overlap of unigrams (single words)

ROUGE-2: Overlap of bigrams (two-word phrases)

ROUGE-L: Longest common subsequence

These metrics compare the model-generated summary with the reference (human-written) summary.

## References

This project was inspired by what I learnt from [Generative AI with Large Language Models](https://www.coursera.org/learn/generative-ai-with-llms) coursework. It was run on [Amazon SageMaker AI](https://aws.amazon.com/sagemaker-ai/?trk=b6c2fafb-22b1-4a97-a2f7-7e4ab2c7aa28&sc_channel=ps&ef_id=CjwKCAjw_pDBBhBMEiwAmY02Nn6IuW1VBZsl5gJYcYgZkHHsW2hwlUNg6_LpX3B7a66lVtj2um506xoCM1UQAvD_BwE:G:s&s_kwcid=AL!4422!3!724218586019!e!!g!!amazon%20sagemaker%20ai!19852662230!170020191325&gad_campaignid=19852662230&gbraid=0AAAAADjHtp9i9BiYxYyVuRr1zKK81GQ2G&gclid=CjwKCAjw_pDBBhBMEiwAmY02Nn6IuW1VBZsl5gJYcYgZkHHsW2hwlUNg6_LpX3B7a66lVtj2um506xoCM1UQAvD_BwE)
