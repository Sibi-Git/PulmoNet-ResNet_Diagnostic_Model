# PulmoNet - ResNet Based Diagnostic Model 🧠💻

PulmoNet is a deep learning-based diagnostic model designed to identify lung conditions such as pneumonia and COVID-19 from medical images. The model uses the ResNet architecture and is integrated with a Flask web application that serves the model through an API using Ngrok for secure tunneling.

![PulmoNet Banner](path_to_your_header_image.png) <!-- Add a relevant banner image here -->

## Table of Contents 📚

- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [API Integration](#api-integration)
- [Model Evaluation](#model-evaluation)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview 🌟

PulmoNet leverages the power of ResNet to analyze CT and MRI scans, providing accurate diagnostic results. This tool is ideal for healthcare professionals seeking to automate the detection of lung conditions.

## Installation 🛠️

### Prerequisites

- Python 3.x 🐍
- TensorFlow 🧠
- Keras ⚙️
- OpenCV 📷
- Numpy ➕
- Matplotlib 📊
- Ngrok 🔗

### Steps

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/Sibi-Git/PulmoNet-ResNet_Diagnostic_Model.git
   cd PulmoNet-ResNet_Diagnostic_Model
   ```

2. **Mount Google Drive (for Colab users):**

   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

3. **Unzip Dataset:**

   ```bash
   !unzip /content/drive/MyDrive/covid_project/dataset.zip -d .
   ```

4. **Install Required Packages:**

   ```bash
   pip install -r requirements.txt
   ```

5. **Install Ngrok:**

   ```bash
   !curl -s https://ngrok-agent.s3.amazonaws.com/ngrok.asc | sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null && echo "deb https://ngrok-agent.s3.amazonaws.com buster main" | sudo tee /etc/apt/sources.list.d/ngrok.list && sudo apt update && sudo apt install ngrok
   pip install pyngrok flask-ngrok
   ```

## Usage 🚀

1. **Preprocess the Data:**

   The data is preprocessed using custom preprocessing classes (`ImageToArrayPreprocessor`, `AspectAwarePreprocessor`, and `SimpleDatasetLoader`) to prepare the images for model input.

2. **Train the Model:**

   ```python
   model = ResNet.build(64, 64, 3, 3, (3, 4, 6), (64, 128, 256, 512), "dataset")
   model.compile(loss="categorical_crossentropy", optimizer=Adam(learning_rate=0.0001), metrics=["accuracy"])
   ```

3. **Save Model Weights:**

   ```python
   checkpoint_filepath='/content/drive/MyDrive/covid_project/resnet_weight.h5'
   ```

4. **Serve the Model with Flask:**

   ```python
   app.run()
   ```

## API Integration 🌐

- **Endpoint:** `/covid`
- **Method:** `POST`
- **Input:** Image URL via request parameters.
- **Output:** JSON response with the predicted class label (`covid`, `ignore`, `normal`).

## Model Evaluation 📈

```python
plt.plot(np.arange(0, 10), H.history["accuracy"], label="train_acc")
plt.plot(np.arange(0, 10), H.history["val_accuracy"], label="val_acc")
```

## Examples 📝

### Running the Flask Application

```bash
python app.py
```

This will start the Flask application and output a public URL (from Ngrok) where the model can be accessed.

### Making a Prediction

```bash
Send a POST request to the Ngrok URL with the image URI to get the diagnosis.
```

## Contributing 🤝

We welcome contributions to PulmoNet! To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m 'Add feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a Pull Request.

## License 📄

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact 📧

- **Email:** msibi.mail@gmail.com
- **LinkedIn:** [Sibi Marappan](https://www.linkedin.com/in/sibi-marappan)
- **GitHub:** [Sibi-Git](https://github.com/Sibi-Git)
