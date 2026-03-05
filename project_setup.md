# 🐍 Ultimate Python Project Setup Guide
Is guide mein step-by-step commands hain ek clean aur professional environment set karne ke liye.
🏗️ Step 1: Project Folder & Git
Sabse pehle folder banayein aur Git initialize karein taake version control shuru ho sake.
# Create and enter folder
mkdir my_awesome_project
cd my_awesome_project

# Initialize Git
git init
❄️ Step 2: Virtual Environment (VENV)
System-wide packages se bachne ke liye isolation zaroori hai.
# Create Environment with latest version of Python installed in your system
python -m venv .venv
# Python specific environment
py --list
py -3.10 -m venv .venv
# Activate (Windows)
.venv\Scripts\activate
# 🚫 Step 3: Create .gitignore
Ye file un cheezon ko rokti hai jo GitHub par nahi jani chahiye. Ek file banayein .gitignore ke naam se:
# Environments
.venv/
env/
venv/

# Environment Variables (Secrets)
.env

# Python Cache & Logs
__pycache__/
*.py[cod]
*.log

# OS Files
.DS_Store
Thumbs.db
🔑 Step 4: Environment Variables (.env)
Apne passwords aur API keys yahan rakhein. Iske liye python-dotenv zaroori hai.
# File: .env
API_KEY=your_secret_key_here
DEBUG=True
PORT=8000
📦 Step 5: Install Packages & Requirements
Jo libraries chahiye wo install karein aur unki list save karein.
# Core Setup (Must have)
pip install python-dotenv

# Choose your framework:
pip install fastapi uvicorn   # For API
pip install streamlit        # For Dashboard/UI

# Save to requirements file
pip freeze > requirements.txt
📝 Step 6: Boilerplate main.py
Ek basic file banayein jo .env ko read karna jaanti ho:
import os
from dotenv import load_dotenv

# Load variables from .env
load_dotenv()

API_KEY = os.getenv("API_KEY")

def main():
    print(f"Project started! Using API Key: {API_KEY}")

if __name__ == "__main__":
    main()
☁️ Step 7: Push to GitHub
Apna setup cloud par save karein.
# Add and Commit
git add .
git commit -m "feat(api): add user profile upload"
# Commit Types
feat=Naya feature ya functionality add karna
feat(api): add user profile upload
fix=Kisi bug ya error ko theek karna
fix(api): error in user profile upload
refactor=Code behtar banana (na feature add ho na bug fix)
refactor(api): refactor user profile upload
chore=Routine tasks (maintenance, .gitignore update)
chore(api): .gitignore update
style=Code ko style ko theek karna
style(api): Code ko style ko theek karna
build=Build system ya external dependencies (pip, npm)
build(api): Build or deployment related changes
test=Testing related changes
test(api): Test related changes
# Push (Change YOUR_USERNAME and REPO_NAME)
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git
git push -u origin main
# 🐳 Step 8: Dockerization (Optional)
Agar project ko containerize karna hai, to Dockerfile banayein:
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "main.py"]
# 💡 Daily Workflow Tips:
Naya package? pip install x -> pip freeze > requirements.txt

Environment activate nahi? Hamesha .venv\Scripts\activate check karein.

Secret change? Sirf .env file edit karein, code ko chherne ki zaroorat nahi.    