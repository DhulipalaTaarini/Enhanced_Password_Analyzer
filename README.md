🔐 Password Strength Classifier using NLP, Entropy & LightGBM
This project presents a hybrid machine learning model that evaluates password strength by combining:
NLP-based semantic embeddings (MiniLM / CodeBERT),
Shannon entropy (information theory),
Time-to-crack analysis using zxcvbn,
and a powerful LightGBM classifier (with optional GPU support).

🧠 Goal: Predict the strength level of a password based on learned features from both statistical and semantic perspectives.

Features:
✅ Uses Hugging Face Transformers (MiniLM or CodeBERT) to extract semantic meaning from passwords.
✅ Calculates password entropy (Shannon entropy) and time-to-crack using zxcvbn.
✅ Efficient batch processing with mixed precision (FP16) and GPU optimization.
✅ LightGBM-based classification with automatic fallback to CPU if GPU unavailable.
✅ Compatible with large password datasets (e.g., PWLDS).

🧩 Architecture Overview
scss
Copy
Edit
Password → [MiniLM Embedding]
         → [Shannon Entropy]
         → [Zxcvbn Crack Time]
         → [Feature Vector]
         → [LightGBM Classifier]
         → Strength Level (0–4)

📊 Dataset
Name: PWLDS (Password Weakness and Leak Detection Set)
Source: Hugging Face
Usage: 500k sampled entries used for training
Columns: Password, Strength_Level


# Install dependencies
pip install -r requirements.txt

Main dependencies:
transformers
torch
zxcvbn
datasets
lightgbm (GPU optional)

🧪 Example Usage:
password = "StrongPass#2024!"
strength = predict_strength(password)
print(f"Predicted Strength: {strength}")
Output:

Predicted Strength Level: 2
Actual Strength Score (zxcvbn): 4
Estimated Crack Time: 3 years
📈 Results
Metric	Score
Accuracy	~0.87
Classifier	LightGBM (GPU/CPU fallback)
Evaluation	80/20 Train-Test Split

Model slightly underestimates strong passwords — can be improved with calibrated labels and better high-strength representation.

Future Improvements: 
✅ Add model calibration for better strength estimation

📊 Normalize entropy and crack-time features

🧪 Include adversarial passwords or real-world leaks

🌐 Build a web-based password strength testing tool

🤝 Contributing
Pull requests are welcome! If you'd like to suggest improvements or add new features, feel free to open an issue or PR.


🙋‍♀️ Author
Taarini
Feel free to connect or fork! 😊
