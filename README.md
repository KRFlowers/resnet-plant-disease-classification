# Evaluating Pre-trained ResNet50V2 for Plant Disease Classification

This project evaluates the performance of a pre-trained ResNet50V2 model for image classification. Using transfer learning with ImageNet weights, I compare its performance against two custom CNN architectures. The models are trained using the New Plant Diseases Dataset from Kaggle.

## Project Overview

**Goal:** Explore how much pre-trained models improve image classification performance compared to training from scratch.

**Approach:** Build the following three deep learning models and compare results:
- Minimal baseline CNN (establish baseline performance)
- Improved CNN with modern techniques (additional layers and regularization)
- ResNet50V2 pre-trained model using transfer learning with frozen ImageNet weights

**Key Finding:** The pre-trained ResNet50V2 achieved 93.4% accuracy. The model outperformed the custom CNN (89.0%) while requiring significantly less training time and architectural tuning.

## Model Results

- **Minimal Baseline CNN:** 10.7% accuracy
- **Improved CNN:** 89.0% accuracy
- **ResNet50V2 Transfer Learning:** 93.4% accuracy
- **ResNet50V2 Tuned:** 95.0% accuracy

**Total improvement:** 10.7% → 95.0% (+84.3 percentage points)

## Lessons Learned

- Image preprocessing proved more complex than model configuration. ResNet50V2 required specific preprocessing (`preprocess_input`), and ensuring compatibility between the preprocessing pipeline and visualization code took more effort than configuring the model itself.

- CNN design improvements (additional layers and dropout regularization) drove the largest performance gains: 10.7% → 89.0%.

- Hyperparameter optimization provided only modest gains (~1.6%), but could be useful in cases where even small improvements are important.

## Technologies Used

**Deep Learning Tools:**
- Implemented models using **TensorFlow 2.x** and **Keras**
- Leveraged **ResNet50V2** pre-trained on **ImageNet** for transfer learning
- Applied **Keras Tuner** with **Bayesian Optimization** for automated hyperparameter search

**Data Pipeline Functions:**
- Loaded images efficiently using `image_dataset_from_directory`
- Applied model-specific preprocessing with `preprocess_input` for ResNet compatibility
- Optimized training performance with dataset caching and prefetching (`tf.data.AUTOTUNE`)


## Dataset

**Source:** [New Plant Diseases Dataset](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset) (Kaggle)

**Note:** The dataset documentation indicates that images were pre-augmented offline. This project did not apply additional augmentation during training.

**Subset Used:** Tomato plant images only
- 10 disease classes (9 diseases + healthy)
- ~22,000 images total (18K train, 4K validation)
- RGB images resized to 224×224 pixels

**Classes:**
- Tomato Bacterial Spot
- Tomato Early Blight
- Tomato Late Blight
- Tomato Leaf Mold
- Tomato Septoria Leaf Spot
- Tomato Spider Mites (Two-spotted)
- Tomato Target Spot
- Tomato Mosaic Virus
- Tomato Yellow Leaf Curl Virus
- Tomato Healthy

## Notebook Structure

**File:** `notebooks/resnet_plant_disease_classification.ipynb`

1. **Configure Environment** - Install packages, import libraries, define helper functions
2. **Load Data** - Build TensorFlow Dataset pipeline with preprocessing
3. **Explore Data** - Analyze class distributions and visualize samples
4. **Develop Models**
   - 4.1: Build minimal baseline CNN 
   - 4.2: Improve CNN architecture 
   - 4.3: Implement ResNet50V2 transfer learning 
   - 4.3.1: Optimize hyperparameters with Keras Tuner
5. **Evaluate Results** - Compare performance across all models
6. **Conclusion** - Review key findings, recommendations, lessons learned

## Quick Start

**Platform:** Google Colab (GPU runtime recommended)

**Setup:**
1. Download the [New Plant Diseases Dataset](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset) from Kaggle
2. Upload to your Google Drive

**Run:**
1. Open `notebooks/resnet_plant_disease_classification.ipynb` in Google Colab
2. Select GPU runtime: Runtime > Change runtime type > GPU
3. Run all cells (notebook mounts Google Drive and loads the dataset)

**Total Runtime:** ~2 hours (hyperparameter tuning: 90 min)

## Future Exploration

- Fine-tune deeper ResNet layers by unfreezing selected blocks
- Compare alternative pre-trained models 
- Expand to full 38-class dataset including all plant types

## References

**Dataset:**  
New Plant Diseases Dataset. (n.d.). Kaggle. https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset

**Documentation:**  
- Keras - Getting Started with KerasTuner. https://keras.io/keras_tuner/getting_started/
- Keras - Transfer Learning Guide. https://keras.io/guides/transfer_learning/
- Keras - ResNet and ResNetV2 API. https://keras.io/api/applications/resnet/
- TensorFlow - Transfer Learning Tutorial. https://www.tensorflow.org/tutorials/images/transfer_learning

## Contact

**Kristi Flowers**  
kristirflowers@gmail.com

**Questions?** Feel free to reach out!
