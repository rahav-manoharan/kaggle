# 🏆 Kaggle Competitions Repository

Welcome to my **Kaggle Competitions** repository! This is where I organize and share code, notebooks, and insights from every Kaggle competition I participate in, starting from **June 24, 2025**. 

Each competition lives in its own dedicated folder with everything from exploratory data analysis (EDA) to final model submissions. Whether you're here to learn, collaborate, or explore, dive right in!

---

## 📁 Repository Structure

Each competition folder follows a consistent naming convention: `YYYY-MM-DD__competition-name` for easy sorting and chronological organization.

```
kaggle/
├── 2025-06-24__example-competition/
│   ├── data/                    # Raw or processed data (usually .gitignored)
│   ├── notebooks/               # Jupyter notebooks for EDA, modeling, etc.
│   │   ├── 01_eda.ipynb
│   │   ├── 02_baseline.ipynb
│   │   └── 03_final_model.ipynb
│   ├── scripts/                 # Python scripts for training, inference, etc.
│   │   ├── train.py
│   │   ├── predict.py
│   │   └── utils.py
│   ├── submissions/             # CSV files submitted to Kaggle
│   ├── models/                  # Saved model files
│   ├── README.md               # Competition-specific documentation
│   └── requirements.txt        # Python dependencies
├── README.md                   # This file
├── .gitignore                  # Exclude large files and sensitive data
└── automation/                 # Scripts for repository automation
    ├── update_competition_log.py
    └── generate_badges.py
```

---

## 🎯 Repository Goals

- **🧠 Learn**: Apply cutting-edge ML and data science techniques
- **🔬 Experiment**: Build reproducible, well-documented workflows  
- **📈 Improve**: Continuously enhance rankings through iterative solutions
- **🤝 Collaborate**: Share knowledge and potentially team up with other Kagglers
- **📚 Document**: Maintain clear records of approaches, failures, and successes

---

## 🚀 Quick Start

To reproduce any competition environment locally:

1. **Clone and navigate to a competition folder:**
   ```bash
   git clone <[your-repo-url](https://github.com/rahav-manoharan/kaggle/>
   cd kaggle/2025-06-24__example-competition
   ```

2. **Set up Python environment:**
   ```bash
   # Create virtual environment
   python -m venv .venv
   
   # Activate environment
   source .venv/bin/activate  # Linux/Mac
   # or
   .venv\Scripts\activate     # Windows
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Download competition data:**
   ```bash
   # Using Kaggle API (requires setup)
   kaggle competitions download -c competition-name -p data/
   ```

---

## 📊 What You'll Find

### Notebooks
- **EDA Notebooks**: Deep dives into data exploration and feature engineering
- **Baseline Models**: Simple models to establish performance benchmarks  
- **Advanced Models**: Ensemble methods, neural networks, and specialized architectures
- **Post-Competition Analysis**: Reflection on what worked and what didn't

### Scripts
- **Training Scripts**: Modular, reproducible model training pipelines
- **Inference Scripts**: Clean prediction generation for submissions
- **Utility Functions**: Reusable code for preprocessing, validation, and visualization
- **Experiment Tracking**: Integration with tools like MLflow or Weights & Biases

---

## 📅 Competition Log

| Date | Competition | Rank | Score | Folder | Key Techniques |
|------|-------------|------|-------|--------|----------------|
| 2025-06-24 | Meta Kaggle Hackathon 🧪 | - | - | `2025-06-24__meta_kaggle_hackathon/` | TBC |

*This table is automatically updated via GitHub Actions - see [automation section](#-automation--badges) below.*

---

## 🤝 Contributing

While this is primarily a personal learning repository, I welcome:

- **🐛 Bug reports**: Found an issue? Open an issue!
- **💡 Suggestions**: Ideas for improvement are always appreciated
- **🔍 Code reviews**: Constructive feedback helps me grow
- **🤝 Collaboration**: Interested in teaming up? Let's connect!

Please check individual competition folders for specific collaboration guidelines.

---

## 📄 License

This repository is licensed under the MIT License. See [LICENSE](LICENSE) for details.

Individual competition folders may have additional licensing requirements based on competition rules and data usage terms.

---

## 🏅 Automation & Badges

### Kaggle Profile & GitHub Stats

![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=Kaggle&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

<!-- Add your actual badges here -->
[![Kaggle Badge](https://img.shields.io/badge/Kaggle-Profile-blue)](https://www.kaggle.com/rahavmanoharan)
[![GitHub Stats](https://github-readme-stats.vercel.app/api?username=rahav-manoharan&show_icons=true&theme=radical)](https://github.com/rahav-manoharan)

### Automated Competition Log Updates

The competition log table is automatically updated using GitHub Actions. Here's how it works:

**Automation Script (`automation/update_competition_log.py`):**
```python
import pandas as pd
import os
from datetime import datetime
import re

def update_competition_log():
    """
    Automatically updates the competition log by scanning folder structure
    and extracting competition information.
    """
    # Scan for competition folders
    competitions = []
    for folder in os.listdir('.'):
        if re.match(r'\d{4}-\d{2}-\d{2}__', folder):
            # Extract date and competition name
            date_str = folder[:10]
            comp_name = folder[12:].replace('-', ' ').title()
            
            # Check for README to get additional info
            readme_path = os.path.join(folder, 'README.md')
            rank, score, techniques = extract_competition_details(readme_path)
            
            competitions.append({
                'Date': date_str,
                'Competition': comp_name,
                'Rank': rank,
                'Score': score,
                'Folder': f"`{folder}/`",
                'Key Techniques': techniques
            })
    
    # Update README.md with new table
    update_readme_table(competitions)

def extract_competition_details(readme_path):
    """Extract rank, score, and techniques from competition README"""
    # Implementation to parse competition-specific README files
    # and extract performance metrics
    pass

def update_readme_table(competitions):
    """Update the main README.md with competition data"""
    # Implementation to replace the table in README.md
    pass

if __name__ == "__main__":
    update_competition_log()
```

**GitHub Actions Workflow (`.github/workflows/update-log.yml`):**
```yaml
name: Update Competition Log

on:
  push:
    branches: [ main ]
  schedule:
    - cron: '0 0 * * 0'  # Weekly on Sunday

jobs:
  update-log:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.9'
    
    - name: Install dependencies
      run: |
        pip install pandas
    
    - name: Update competition log
      run: |
        python automation/update_competition_log.py
    
    - name: Commit changes
      run: |
        git config --local user.email "action@github.com"
        git config --local user.name "GitHub Action"
        git add README.md
        git diff --staged --quiet || git commit -m "🤖 Auto-update competition log"
        git push
```

### Badge Generation

**Dynamic Kaggle Stats Badge:**
```python
# automation/generate_badges.py
import requests
import json

def generate_kaggle_stats_badge(username="rahavmanoharan"):
    """
    Generate a dynamic badge showing Kaggle competition stats
    """
    # Use Kaggle API to fetch user stats
    url = f"https://www.kaggle.com/api/v1/users/{username}"
    # Implementation to fetch and format stats
    pass

def update_readme_badges():
    """
    Update README.md with current badge information
    """
    # Implementation to update badge section
    pass
```

---

## 🔗 Connect & Follow

- **Kaggle**: [Your Kaggle Profile](https://www.kaggle.com/rahavmanoharan)
- **LinkedIn**: [Your LinkedIn](https://linkedin.com/in/rahav-manoharan)
- **GitHub**: [Your GitHub](https://github.com/rahav-manoharan)

---

*Happy Kaggling! 🚀*
