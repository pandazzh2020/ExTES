
## Data

The data file is `ExTES.json`.

### Statistics
<font size=1>

#### Scenarios
| Scenarios| Number   | Proportion   | Scenarios| Number   | Proportion   |
| :--------------  | :------- | :------- | :--------------  | :------- | :------- |
|Breakups or Divorce| 710 |6.3%   |Navigating Gender Identity and Transitioning |202 |1.8%|
|Conflicts or Communication Problems|1,109 |9.9%   |Moving to a New City or Country |202 |1.8%|
|Communication Challenges| 1,008 |9.0%  |Career Transitions |202 |1.8%|
|Coping with the Death of a Loved One|593 |5.3%  |Parenthood and Parenting Challenges |202 |1.8%|
|Dealing with the Loss of a Pet|601 |5.4%  |Low Self-Esteem or Lack of Confidence |302 |2.7%|
|Work-related Stress and Burnout|403 |3.6%  |Body Image Concerns and Eating Disorders |101 |0.9%|
|Financial Worries and Uncertainty|403 |3.6%  |LGBTQ+ Identity |101 |0.9%|
|Unemployment-related Stress|403 |3.6%  |Cultural Identity and Belonging |101 |0.9%|
|Academic Stress|403 |3.6%  |Academic Stress or Pressure |202 |1.8%|
|Spirituality and Faith|202 |1.8%  |Job Loss or Career Setbacks |202 |1.8%|
|Managing Bipolar Disorder|202 |1.8%  |Parenting Challenges and Parental Guilt |202 |1.8%|
|Anxiety and Panic|202 |1.8%  |Sibling Rivalry or Family Conflict |403 |3.6%|
|Depression and Low Mood|403 |3.6%  |Surviving and Recovering from Physical or Emotional Abuse |101 |0.9%|
|Adjusting to a New Job or Role|302 |2.7%  |Healing from Sexual Assault or Domestic Violence |101 |0.9%|
|Chronic Illness or Pain Management|302 |2.7%  |Post-Traumatic Stress Disorder (PTSD) |101 |0.9%|
|Coping with a Diagnosis or Medical Treatment|202 |1.8%  |Healing from Abuse |202 |1.8%|
|Caregiver Support|202 |1.8%  |Addiction and Recovery |202 |1.8%|
|Finding Meaning and Purpose in Life|202 |1.8%  |Support for Loved Ones or Friends |202 |1.8%|
</font>

<font size=1>

#### Strategy Category 
| Strategy Category| Number   | Proportion   |
| :--------------  | :------- | :------- |
|Reflective Statements (RS)| 14,560 | 14.8% |
|Clarification (Cla)| 2,898| 2.9%|
|Emotional Validation (EV)| 19,367| 19.8%|
|Empathetic Statements (ES)| 8,482| 8.7%|
|Affirmation (Aff)| 16,539| 16.9%|
|Offer Hope (OH)| 4,665| 4.8%|
|Avoid Judgment And Criticism (AJC)| 1,767| 1.8%|
|Suggest Options (SO)| 6,079| 6.2%|
|Collaborative Planning (CP)| 3,534| 3.6%|
|Provide Different Perspectives (PDP)| 3,322| 3.4%|
|Reframe Negative Thoughts (RNT)| 2,050 | 2.1%|
|Share Information (SI)| 3,181| 3.3%|
|Normalize Experiences (NE)| 2,403| 2.6%|
|Promote Self-Care Practices (PSP)| 2,686| 2.7%|
|Stress Management (SM)| 2,474| 2.5%|
|Others (Oth)| 3887| 3.9%|
|**Overall**| 97,893| 100%|

</font>



## How to run
### 1. Use pip to install dependent libraries, enter the project directory, and use the following commands to install:

`pip install -r requirements.txt`

### 2. Here we want to fine-tune the instructions based on LLAMA-7B, so we must first download the model weights and perform a series of conversions. Switch to the location of the project and use the following command to download the weights:

`python scripts/download.py --repo_id openlm-research/open_llama_7b --local_dir checkpoints/open-llama/7B`

### 3. Use the following command to convert.After the conversion, you will get a lit-llama.pth file with a size of about 26G

`python scripts/convert_hf_checkpoint.py --checkpoint_dir checkpoints/open-llama/7B --model_size 7B`

### 4. At the command line, run the test run with the following command:

`python generate.py --prompt "hello"`

### 5. Use the ExTES dataset for fine-tuning, and use the following instructions to preprocess the dataset:

`python scripts/prepare_any_text.py`

### 6. Use the following commands to fine-tune. After training, you will get a series of lora weight files in out/lora/extes

`python finetune/lora.py`



