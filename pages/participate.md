## Introduction: Emergency Audio Event Detection
Authors: Nazim Fadli (M2DS), Soumodeep Hoodaty (M2DS), Clijo Jose (M2DS), Sergei Gerasimov (M2DS), Luis Miguel Herrá Alpuente, Imane Mokhtatif (M2DS).

The goal of this challenge is to build models capable of automatically detecting and segmenting emergency sounds from everyday background noise. 

![Audio Spectrogram Example](https://media.geeksforgeeks.org/wp-content/uploads/20200725122651/image121.png)

### The Task
Given a dataset of mixed audio clips, your model must:
* **Detect** whether an emergency sound occurs.
* **Segment** the event by predicting its exact **start and end times**.

*(Note: If no emergency is present in the clip, the model should simply return an empty result.)*

### Why it Matters
This is a complex challenge because models must simultaneously *recognize* the type of sound and *locate* it precisely in time. Solving this is crucial for advancing real-world applications like autonomous driving, public safety monitoring, smart city infrastructure, and assistive technologies.

**Mel-Spectrogram Comparison**
*(Visualizing the non-linear frequency energy distributions)*

<img src="https://raw.githubusercontent.com/Nazim-fad/Emergency-Audio-Event-Detection-Challenge/refs/heads/main/assets/spectograms.png" alt="Mel-Spectrogram Comparison" width="700">

**Reference Audio Samples**
*(Auditory verification of the Signal-to-Noise Ratio and environmental distortion)*

**1. Emergency Event Present**
[Listen to the Emergency Audio 🔊](https://cdn.jsdelivr.net/gh/Nazim-fad/Emergency-Audio-Event-Detection-Challenge/assets/emergency_noise.wav)

**2. Strictly Background Audio**
[Listen to the Background Audio 🔊](https://cdn.jsdelivr.net/gh/Nazim-fad/Emergency-Audio-Event-Detection-Challenge/assets/bg_noise.wav)


## How to Participate
Ready to build your solution? Here is everything you need to know to format and submit your model successfully.

### 1. The Submission File
Participants must submit a single Python file named **`submission.py`**. 

Inside this file, you must define a `get_model()` function that returns your core model object. 

### 2. Required Model Methods
Your model object must implement the following two methods:

* **`fit(train_features, train_labels, data_dir)`:** Use this to train your model on the provided dataset.
* **`predict(audio_path)`:** Use this to process an audio file and return the timestamps of detected emergency segments.

### 3. Expected Output Format
The `predict` method must return a list of dictionaries. Each dictionary represents a detected emergency segment and must contain `start` and `end` keys. 

**Example: Emergencies detected**
```python
[
    {"start": 0.5, "end": 1.7},
    {"start": 3.2, "end": 4.0}
]

```

**Example: No emergency detected**
If the model does not detect anything in the audio file, simply return an empty list:

```python
[]

```

### 4. Evaluation
Predicted time segments are compared with the ground-truth annotations using **Intersection over Union (IoU)**. A prediction is considered correct if the overlap with a true segment exceeds a predefined threshold.

The main evaluation metrics are:
* **Segment Precision:** The proportion of predicted segments that correctly match a true emergency segment.
* **Segment Recall:** The proportion of true emergency segments that are successfully detected.
* **Segment F1-score (Primary Leaderboard Metric):** The harmonic mean of precision and recall.

We also report **presence-level metrics (F1 score and accuracy)**, which evaluate whether a model correctly predicts if an emergency occurs in each audio clip.

### 5. Resources
To help you get started, we provide the full dataset and a starter kit for local development.

- **Download the data and starting kit:** [Google Drive](https://drive.google.com/file/d/1JDf49a_nB_tjWqBQfBafq2A6Q6kOepZu/view?usp=sharing)
- **Challenge repository and additional information:** [GitHub Repository](https://github.com/Nazim-fad/Emergency-Audio-Event-Detection-Challenge)

The Google Drive folder contains the data and starter resources needed to begin experimenting locally.  
The GitHub repository includes additional information about the challenge, updates, and useful project files.

We encourage participants to review both before starting their submissions. Good luck, and we look forward to seeing your solutions!
