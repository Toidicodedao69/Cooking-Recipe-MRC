# Cooking-Recipe-MRC
This is a large language model fine-tuned on a cooking dataset (in SQuAD 1.0 format) for the specific use case of Machine Reading Comprehension (MRC), or Extractive Question Answering. The deployed model can be accessed through this [HuggingFace's Space](https://huggingface.co/spaces/Hieu-Pham/Cooking-Recipe-MRC).

![UI of the Deployed Model](model_ui.png)

## Technologies Details 
+ **Base Model**: [Meta's Llama2-7B-hf model](https://huggingface.co/meta-llama/Llama-2-7b-hf)
+ **Environment**: Google's Colab
+ **Main Framework/Library**:
  - Development: Hugging Face + PyTorch
  - Evaluation: Hugging Face + Sklearn.metrics
  - Deployment: Gradio
 
## Finetuning Details
+ The recipe dataset used for fine-tuning the model was split into 80% training (1.79k rows), 10% validation (224 rows), and 10% test (225 rows). The dataset was uploaded to [Hugging Face](https://huggingface.co/datasets/Hieu-Pham/cooking_squad_splitted)
+ Fine-Tuning Techniques: [QLoRA](https://arxiv.org/abs/2305.14314) & [IA3](https://arxiv.org/abs/2205.05638)
+ Fine-tuning Configurations can be found in the Notebooks folder.
+ 2 main approaches used for model predictions:
  - **Extractive QA**: Predicts the answer's position inside the given context.
  - **Causal LM**: Predicts (Generates) the answer based on the given context and question.
  **Differences between the 2 approaches are further explained in this [video](https://youtu.be/UE6FPYfwWuE)**

## Evaluation Results
Exact-Match and F1 score metrics were used to evaluate the fine-tuned model. The following table shows the evaluation results of the Causal LM models. 

|Metric     | Base Model         | QLoRA  | IA3
| ------------- |:-------------:| -----:| ---
| Exact-Match Score     | 2. 67 | 13.78 | 8.45
| F1 Score      | 65.45     |   76.13 | 71.41

The visualizations of the results using Power BI can be found [here](/"Prediction Sets (Causal LM)"/"Custom Prompting"/"Results Visualization.pbix")

Evaluation of the Extractive QA models was not successful because the Llama models were not supported for the task of extractive QA on Hugging Face

**All fine-tuned models and adapters were uploaded to my [Hugging Face profile](https://huggingface.co/Hieu-Pham)**
