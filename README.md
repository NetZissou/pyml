# pyml

## Working Environment

To recreate the working environment for this repo:
```
# Create a python virtrual environment
python -m venv venv

# Exclude venv from version control
echo "venv/" >> .gitignore

# Activate the virtual environment
source venv/bin/activate

# Snapshot the current working environment
pip freeze > requirements.txt

# Rebuild the working environment
pip install -r requirements.txt
```