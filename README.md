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
```


This structure includes information such as the `country_code`, `postal_code`, `place_name`, administrative divisions (`admin_name1`, `admin_name2`, `admin_name3`), and geographical coordinates (`latitude`, `longitude`).

---

## Examples

Here are some practical examples on how to use the JSON data in a web application:

### 1. Load Data from a JSON File

You can load the JSON file (e.g., `TR.json` for Turkey) in your web application using JavaScript's `fetch()` method.

#### Example: Fetch Data for Turkey

```javascript
fetch('./data/TR.json')
  .then(res => res.json())
  .then(data => {
    console.log(data);  // Logs the entire data object for Turkey (TR.json)
  })
  .catch(error => console.error('Error loading data:', error));
```

This code will fetch the data from the `TR.json` file and log the response to the console.

---

### 2. Query Data by Postal Code

To search for a specific postal code within the JSON data, use the `find()` method to filter the data.

#### Example: Query by Postal Code

```javascript
fetch('./data/TR.json')
  .then(res => res.json())
  .then(data => {
    const result = data.find(entry => entry.postal_code === '02700');
    console.log(result);  // Logs data for postal code "02700"
  })
  .catch(error => console.error('Error fetching data:', error));
```

This will find and log the data for the postal code `02700`, which corresponds to "Çobanpinari" in Turkey.

---

### 3. Display Data in a Table

You can also display the data in a table format on a webpage. Here's how you can create a simple table using the data.

#### Example: Display Data in a Table

```html
<table id="postalTable">
  <thead>
    <tr>
      <th>Postal Code</th>
      <th>Place Name</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<script>
  fetch('./data/TR.json')
    .then(res => res.json())
    .then(data => {
      const tableBody = document.querySelector('#postalTable tbody');
      data.forEach(entry => {
        const row = document.createElement('tr');
        row.innerHTML = `
          <td>${entry.postal_code}</td>
          <td>${entry.place_name}</td>
          <td>${entry.latitude}</td>
          <td>${entry.longitude}</td>
        `;
        tableBody.appendChild(row);
      });
    })
    .catch(error => console.error('Error fetching data:', error));
</script>
```

This will fetch the data from `TR.json` and dynamically populate a table with postal code, place name, latitude, and longitude.

---

### 4. Query by Place Name

You can query the JSON data by a place name and get the matching postal codes.

#### Example: Query by Place Name

```javascript
fetch('./data/TR.json')
  .then(res => res.json())
  .then(data => {
    const placeName = 'Çobanpinari';  // Change this to the desired place name
    const results = data.filter(entry => entry.place_name === placeName);
    console.log(results);  // Logs all results matching "Çobanpinari"
  })
  .catch(error => console.error('Error fetching data:', error));
```

