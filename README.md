BondedCycles/
├── README.md
├── data/
│ └── cycles.json
└── src/
└── tracker.py


## 💻 Installation
1. Install Python 3.8+
2. Clone the repo:  
   ```bash
   git clone https://github.com/yourusername/BondedCycles.git

cd BondedCycles

python src/tracker.py


---

### 2️⃣ `data/cycles.json`
```json
{
  "mother": [],
  "daughter": []
}

import json
from datetime import datetime, timedelta
import os

DATA_FILE = "data/cycles.json"

def load_data():
    if not os.path.exists(DATA_FILE):
        return {"mother": [], "daughter": []}
    with open(DATA_FILE, "r") as f:
        return json.load(f)

def save_data(data):
    with open(DATA_FILE, "w") as f:
        json.dump(data, f, indent=4)

def add_cycle(user, date_str):
    try:
        date = datetime.strptime(date_str, "%Y-%m-%d")
    except ValueError:
        print("Invalid date format. Use YYYY-MM-DD.")
        return
    data[user].append(date_str)
    save_data(data)
    print(f"{user.capitalize()}'s cycle added: {date_str}")

def predict_next_cycle(user):
    if not data[user]:
        print(f"No cycle data for {user}.")
        return
    last_cycle = datetime.strptime(data[user][-1], "%Y-%m-%d")
    next_cycle = last_cycle + timedelta(days=28)
    print(f"Next cycle for {user} is expected on {next_cycle.date()}")

def main():
    print("Welcome to BondedCycles!")
    while True:
        action = input("Choose: [add/view/predict/quit] ").strip().lower()
        if action == "quit":
            break
        user = input("Who? [mother/daughter] ").strip().lower()
        if user not in data:
            print("Invalid user.")
            continue
        if action == "add":
            date_str = input("Enter cycle start date (YYYY-MM-DD): ")
            add_cycle(user, date_str)
        elif action == "view":
            print(f"{user.capitalize()}'s cycles: {data[user]}")
        elif action == "predict":
            predict_next_cycle(user)
        else:
            print("Unknown action.")

if __name__ == "__main__":
    data = load_data()
    main()

import json
from datetime import datetime, timedelta
import os

DATA_FILE = "data/cycles.json"

def load_data():
    if not os.path.exists(DATA_FILE):
        return {"mother": [], "daughter": []}
    with open(DATA_FILE, "r") as f:
        return json.load(f)

def save_data(data):
    with open(DATA_FILE, "w") as f:
        json.dump(data, f, indent=4)

def add_cycle(user, date_str):
    try:
        date = datetime.strptime(date_str, "%Y-%m-%d")
    except ValueError:
        print("Invalid date format. Use YYYY-MM-DD.")
        return
    data[user].append(date_str)
    save_data(data)
    print(f"{user.capitalize()}'s cycle added: {date_str}")

def predict_next_cycle(user):
    if not data[user]:
        print(f"No cycle data for {user}.")
        return
    last_cycle = datetime.strptime(data[user][-1], "%Y-%m-%d")
    next_cycle = last_cycle + timedelta(days=28)
    print(f"Next cycle for {user} is expected on {next_cycle.date()}")

def main():
    print("Welcome to BondedCycles!")
    while True:
        action = input("Choose: [add/view/predict/quit] ").strip().lower()
        if action == "quit":
            break
        user = input("Who? [mother/daughter] ").strip().lower()
        if user not in data:
            print("Invalid user.")
            continue
        if action == "add":
            date_str = input("Enter cycle start date (YYYY-MM-DD): ")
            add_cycle(user, date_str)
        elif action == "view":
            print(f"{user.capitalize()}'s cycles: {data[user]}")
        elif action == "predict":
            predict_next_cycle(user)
        else:
            print("Unknown action.")

if __name__ == "__main__":
    data = load_data()
    main()


