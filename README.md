# Using LSTMs to Model Naturalistic fMRI Data

## Project Overview

This repository contains the project files for our **NeuroMatch Academy** project titled "Using LSTMs to Model Naturalistic fMRI Data." The project aimed to model the temporal properties of naturalistic fMRI data using **Long Short-Term Memory (LSTM)** networks to gain deeper insights into brain regions activated during naturalistic tasks.

### Team Members
- **Akhila Sankaramanchi**
- **Ariadne Letrou**
- **Brandon Carone**

Group name: **Temporal Titans**

## Project Aims and Research Questions

1. **How can we use deep learning to model the temporal properties inherent in naturalistic fMRI?**
2. **How can this effort afford deeper insights into brain regions implicated in naturalistic tasks?**

Our main goal was to build a model that incorporates the **temporal properties** of naturalistic fMRI data and use it to map **brain activity to behavior**.

## Background

Traditional fMRI experiments typically involve having participants engage in specific tasks (e.g., viewing a series of images), and brain activity is measured in response to each individual stimulus. However, recent approaches involve **naturalistic paradigms**—continuous stimuli like movies or narratives that mimic real-world experiences more closely.

**Naturalistic fMRI data** poses challenges for traditional analysis methods, as they are often agnostic to temporal information. To address this, we built an LSTM-based model capable of capturing the **temporal dynamics** of brain activity over time.

## Dataset

- **Participants**: 100 individuals
- **Stimuli**: 10 videos per participant (5 featuring meaningful interactions and 5 with random movements)
- **Brain Regions of Interest (ROIs)**:
  - **Temporo-Parietal Junction (TPJ)**: Linked to **Theory of Mind** tasks.
  - **Early Auditory Cortex**: Used as a **control region**.
- **Data Shape**: Voxels × Time

The dataset was derived from open-source fMRI data, focusing on **Theory of Mind** tasks where participants watched videos of shapes interacting either meaningfully or randomly.

## Model Choice: Why LSTMs?

- We used **Long Short-Term Memory (LSTM)** networks because they effectively model **temporal dependencies** in sequential data. 
- The **temporal dynamics** inherent in fMRI sequences can be tracked by LSTMs, which allows the model to retain important information over longer sequences.
- LSTMs are suitable for our use case due to their ability to selectively remember or forget information, thus managing long-term dependencies without issues like vanishing gradients.

## Methods

- **Model Architecture**: A 3-layer LSTM with hidden sizes of 23, 10, and 5, respectively.
- **Regularization**:
  - **Dropout** rate of 0.6 to reduce overfitting.
  - **Early Stopping** with a patience of 10 epochs.
- **Implementation**: Hyperparameter tuning was used to determine the optimal architecture and training settings.

## Results

1. **Overfitting Observed Initially**:
   - A simpler LSTM model (with 2 layers) was prone to overfitting due to the small dataset.
2. **Regularization Improvements**:
   - Adding **dropout** and **early stopping** mitigated overfitting to some extent, with training and testing accuracies approaching 80%.
   - Using **L2 regularization** was not very effective, so it was removed.
3. **Optimal Configuration**:
   - A **3-layer LSTM** with dropout and early stopping provided the best balance between complexity and generalization.
4. **Task-Selective Performance**:
   - The model performed well on the **TPJ region**, suggesting its capacity to identify **task-relevant brain regions**.
   - Poorer performance was observed on unrelated regions (e.g., the auditory cortex), indicating that the model was indeed learning task-specific information.

## Discussion

- **Utility of LSTMs**: LSTMs are effective for modeling the **temporal structure** of naturalistic fMRI data.
- **Model Limitations**:
  - The model struggled with overfitting, especially with more complex architectures.
  - Regularization techniques like **dropout** and **early stopping** helped, but further improvements could be made.
- **Future Work**:
  - Experiment with other regularization techniques, such as **data augmentation** (e.g., time stretching, filtering, adding Gaussian noise).
  - Incorporate more data to enhance the model's robustness and reduce overfitting.

## References

- Barch D. M. et al. (2013). Function in the human connectome: Task-fMRI and individual differences in behavior. *NeuroImage*, 80, 169–189. [https://doi.org/10.1016/j.neuroimage.2013.05.033](https://doi.org/10.1016/j.neuroimage.2013.05.033)
- Saxe R. & Wexler A. (2005). Making sense of another mind: The role of the right temporo-parietal junction. *Neuropsychologia*, 43(10), 1391–1399. [https://doi.org/10.1016/j.neuropsychologia.2005.02.013](https://doi.org/10.1016/j.neuropsychologia.2005.02.013)
- Olszowy W., Aston J., Rua C., et al. Accurate autocorrelation modeling substantially improves fMRI reliability. *Nat Commun*, 10, 1220 (2019). [https://doi.org/10.1038/s41467-019-09230-w](https://doi.org/10.1038/s41467-019-09230-w)

## Acknowledgements

We would like to thank our TAs (Ozgur & Soan), our mentor (Di), and our POD members (Colleen, John, Ian, Philipp, & Tuga) for their guidance throughout the project.

---

This project was conducted as part of the **NeuroMatch Academy**, with contributions from **Temporal Titans**: Akhila Sankaramanchi, Ariadne Letrou, and Brandon Carone.
