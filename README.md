# 🌍 jsongeocode

A collection of postal code and geolocation data for 95 countries in easy-to-use JSON format.  



## 📦 What's Inside?

Each country has its own JSON file for modular access and performance:
- `TR.json` → Turkey
- `US.json` → United States
- `DE.json` → Germany
- `FR.json` → France
- ...

A total of **95 countries** are included.

### 📁 Sample Data Format (`TR.json`):

```json
[
  {
    "country_code": "TR",
    "postal_code": "02700",
    "place_name": "Çobanpinari",
    "admin_name1": "Adiyaman",
    "admin_code1": "02",
    "admin_name2": "Gerger",
    "admin_code2": "8631677",
    "admin_name3": "",
    "admin_code3": "",
    "latitude": "38.0161",
    "longitude": "38.9902",
    "accuracy": "3"
  }
]


🔍 How to Use (Web Example)
You can load country data in your web app using fetch():

fetch('./data/TR.json')
  .then(res => res.json())
  .then(data => {
    const result = data.find(entry => entry.postal_code === '02700');
    console.log(result.place_name); // Output: Çobanpinari
  });
