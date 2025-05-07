# Pose Estimation and Classification for Combat Sports using Vision Transformers

This project presents a pipeline for pose-based classification of combat interactions in Brazilian Jiu-Jitsu (BJJ). We use a Vision Transformer (ViT) to classify dual-person pose encodings into 18 interaction classes and support real-time inference through Mediapipe and a lightweight MLP. Our approach achieves state-of-the-art performance on the Brazilian Jiu-Jitsu Positions Dataset.

## Project Highlights

- **Model Architecture**: Transformer-based classifier trained on spatial pose keypoints for 2-person interactions.
- **Dataset**: [Brazilian Jiu-Jitsu Positions Dataset](https://vicos.si/resources/jiujitsu/) with 120,279 annotated images across 18 classes.
- **Experiments**:
  - Baseline model: Shallow Transformer with basic embeddings.
  - Iteration 2: Better initialization, data preprocessing refinements.
  - Final Model: Grouped Query Attention, deeper layers, improved positional encoding.
- **Performance**: Achieved up to **97% test accuracy** on pose classification task.
- **Real-time Inference**: Integrated [MediaPipe](https://google.github.io/mediapipe/) for live keypoint extraction and prediction using a fast MLP.
- **Visualization**: Output image overlays with predicted class labels and confidence scores.

## Dataset

We use the publicly available [Brazilian Jiu-Jitsu Positions Dataset](https://vicos.si/resources/jiujitsu/), which contains labeled image frames showing two athletes in various combat positions. These include:
- Mount, Back Mount, Turtle, Side Control, Knee on Belly, Guard Variants, etc.
- 18 total interaction classes across 10 core positional states.

## Real-Time Application

We extended our pipeline for real-time pose prediction using webcam input:
- MediaPipe extracts 34 keypoints per frame (17 per person).
- The keypoints are reshaped to a `[2, 34]` format and passed to a trained MLP.
- The system outputs real-time predictions with confidence values for combat class.

> Demo: See `output.png` and `realtime_demo.gif` for qualitative examples from our university dorm.

## 📁 Project Structure


├── BaselineModel.ipynb
├── Improvement1.ipynb
├── Improvement2.ipynb     #main final model
├── pose_transformer.pth   #saved model
├── real_time_bjj_detection.ipynb
├── README.md
└── requirements.txt


## 📈 Results

- **Test Accuracy**: 97%
- **Confusion Matrix**: Available in `results/`
- **Qualitative Visualizations**: Overlays of predicted vs actual classes with confidence.

##  Experiments Summary

| Experiment | Description                              | Accuracy |
|------------|------------------------------------------|----------|
| Baseline   | Basic Transformer, default init          | 94%      |
| Iteration 2| Improved preprocessing, better init      | 95%      |
| Final      | GQA, increased depth, RoPE embeddings     | **97%**  |

## 🔗 Resources

- 📁 Dataset: [Brazilian Jiu-Jitsu Positions](https://vicos.si/resources/jiujitsu/)
- 📚 Paper Reference: [Video-Based Detection of Combat Positions](https://vicos.si/resources/jiujitsu/)
- 💻 GitHub Repo: [github.com/tk1475/BJJ-Pose-Estimation](https://github.com/tk1475/BJJ-Pose-Estimation)

## 🧑‍💻 Authors

- **Ahmed Hassan** — [26100308@lums.edu.pk](mailto:26100308@lums.edu.pk)
- **Basil Hassan** — [26100303@lums.edu.pk](mailto:26100303@lums.edu.pk)
- Department of Computer Science, Lahore University of Management Sciences

## 📜 Citation

If you use this code or dataset, please cite:

```bibtex
@misc{hudovernik2021jiujitsu,
  title={Video-Based Detection of Combat Positions and Automatic Scoring in Jiu-jitsu},
  author={Valter Hudovernik and Danijel Skočaj},
  year={2021},
  url={https://vicos.si/resources/jiujitsu/}
}
