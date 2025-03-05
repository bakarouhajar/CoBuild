# CoBuild

# Project Setup

## Initializing the Submodules
This project uses Git submodules to manage the frontend and backend as separate repositories. To properly set up the project, follow these steps:

### **1. Clone the Repository with Submodules**
```sh
git clone --recurse-submodules https://github.com/bakarouhajar/CoBuild.git
```
If you already cloned the repository without submodules, run:
```sh
git submodule update --init --recursive
```

### **2. Pull the Latest Changes from Submodules**
Whenever there are updates in the submodules (frontend/backend), update them using:
```sh
git submodule update --remote --merge
```

### **3. Committing Submodule Updates**
If you make changes in a submodule and want to update the reference in the parent repository:
```sh
cd frontend  # or cd backend

git pull origin main  # Pull the latest changes

cd ..
git add frontend  # or git add backend
git commit -m "Updated submodule to latest commit"
git push origin main
```

### **4. Removing a Submodule (If Needed)**
If you need to remove a submodule:
```sh
git submodule deinit -f frontend  # or backend
rm -rf .git/modules/frontend  # or backend
git rm -f frontend  # or backend
git commit -m "Removed frontend submodule"
git push origin main
```

### **5. Extra Notes**
- Ensure that each submodule repository has the necessary dependencies installed (e.g., `npm install` for frontend, `pip install -r requirements.txt` for backend).
- If switching branches that involve submodule changes, use:
  ```sh
  git checkout branch-name --recurse-submodules
  