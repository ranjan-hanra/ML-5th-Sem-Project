# ML-5th-Sem-Project
## 🚀 Running on Google Colab

Follow these steps to clone the repository, execute the environment commands, and download your data file directly inside a Google Colab notebook.

### Step 1: Open a Blank Notebook
Go to [Google Colab](https://google.com) and click on **New Notebook**.

---

### Step 2: Clone the Repository
Copy and paste the following code block into your first Colab cell and run it (press `Shift + Enter`) to clone your forked folder:

```python
# Clone the repository
!git clone <PASTE_YOUR_FORKED_REPOSITORY_URL_HERE>

# Move into the project directory
%cd <PROJECT_FOLDER_NAME>
```

---

### Step 3: Run the Commands
Create a new code cell, paste the following commands, and execute them **one by one** (or all at once) to run the setup:

```python
# 1. Install required packages
!pip install -r requirements.txt

# 2. Run the setup script
!python setup.py

# 3. Run the main execution script
!python main.py
```

---

### Step 4: Download the CSV File
Once the scripts finish executing, the file **`KT_GameBox_1.csv`** will be generated. Run this cell to download the file directly to your local computer:

```python
from google.colab import files

# Download the generated data file
files.download('KT_GameBox_1.csv')
```
*(Alternatively, you can click the **Folder icon** on the left sidebar of Colab, locate `KT_GameBox_1.csv`, click the three dots next to it, and select **Download**).*
