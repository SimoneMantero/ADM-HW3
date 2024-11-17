# ADM-HW3
Third homework of the "Algorithmic Methods of Data Mining" class (Sc.M. in Data Science)


# Advanced Search Engine for Michelin Restaurants

**Homework 3** focus is to create a search engine for Michelin restaurants in Italy.  It includes steps such as data collection, web scraping, indexing, and search functionalities. The project is structured into 5 key steps as detailed below:

---

### **1. Data Collection**
#### **1.1 Get the List of Michelin Restaurants**
We scraped the Michelin Guide website to collect URLs for approximately **2,000 restaurants** in Italy. These URLs were saved in a `links.txt` file, with one URL per line.

#### **1.2 Crawl Michelin Restaurant Pages**
We downloaded and saved the HTML pages for all the restaurant URLs. These pages were stored in pages/ folder and then organized into subfolders (`page1`, `page2`, etc.) based on the Michelin Guide’s pagination.

#### **1.3 Parse Downloaded Pages**
We extracted the following structured data from the HTML pages:
- **restaurantName**: Name of the restaurant.
- **address**: Full address.
- **city**: City of the restaurant.
- **postalCode**: Postal code.
- **country**: Country (Italy).
- **priceRange**: Price range (€, €€, €€€, €€€€).
- **cuisineType**: Cuisine type offered.
- **description**: Short description of the restaurant.
- **facilitiesServices**: List of facilities and services provided (e.g., Wi-Fi, terrace).
- **creditCards**: List of accepted credit cards (e.g., Visa, Mastercard, Amex).
- **phoneNumber**: Contact number.
- **website**: Restaurant’s website.

Then we built a DataFrame with these data.

The parsed data was saved as **TSV files** in the `tsv_files/` folder and consolidated into a dataset (`restaurants.csv`) for further analysis.

---

### **2. Search Engine**
#### **2.0 Preprocessing**
We cleaned the text in restaurant descriptions by:
- Removing stopwords and punctuation.
- Converting text to lowercase.
- Applying stemming for better term matching.

#### **2.1 Conjunctive Query**
We implemented a search engine that builds a **vocabulary** and **inverted index** for restaurant descriptions.
  
#### **2.2 Ranked Search Engine with TF-IDF and Cosine Similarity**
We enhanced the search engine by ranking results based on **TF-IDF** and **Cosine Similarity**:
1. Calculated **TF-IDF scores** for terms in the descriptions.
2. Ranked restaurants based on their similarity to the query.

---

### **3. Define a New Score!**
We developed a **custom scoring function** to improve ranking:
1. Weighted attributes:
   - **Description Similarity**
   - **Cuisine Type Match**
   - **Facilities and Services**
   - **Price Range Affordability**
2. Used a **heap data structure** to maintain the top-k results.

---

### **4. Visualizing the Most Relevant Restaurants**
We visualized the restaurant data on interactive maps:
- **Restaurants by Location**: Displayed on a map using cities and regions.
- **Price Range Encoding**: Used color-coding to represent price ranges (€ to €€€€).
- **Top-K Restaurants**: Highlighted top results based on custom scoring.

---

### **5. BONUS: Advanced Search Engine**
We extended the search engine to the advanced filtering:
1. **Search Criteria**: Users can filter by:
   - **restaurantName**
   - **city**
   - **cuisineType**
2. **Advanced Filters**:
   - **Price Range**: Select affordability levels (€ to €€€€).
   - **Region**: Limit search to specific Italian regions.
   - **Accepted Credit Cards**: Filter by card types (Visa, Mastercard, Amex).
   - **Facilities and Services**: Look for amenities like Wi-Fi, terrace, or parking.

---

### **Algorithmic Question**
We solved a problem where a robot collects packages in a grid by sorting the coordinates lexicographically `(x, y)` and traversing in the smallest lexicographical path (`U`, `R`).

- **Complexity**: `$O\left(\frac{n}{\log(n)}\right)$ for sorting and $O(n)$ for traversal.  
- **Optimality**: Sorting ensures the shortest path, and lexicographical order guarantees consistent movement.


---

**Collaborators**
Camilla Labbate,
Elena Di Grigoli,
Federico Lattanzio,
Simone Mantero

We suggest to open the file on Visual Studio and to run the codes to see the interactive graphs.

## **Repository Structure**
- **`pages/`**: Contains downloaded HTML pages of restaurants.
   - Organized into subfolders like `page1`, `page2`, etc., based on the Michelin Guide pagination.
- **`tsv_files/`**: Stores TSV files with parsed restaurant data.
- **`LICENSE`**: Project license.
- **`README.md`**: Documentation for the project.
- **`colored_italy_city_restaurant_map.html`**: Interactive map with color-coded price ranges.
- **`inverted_index.json`**: Stores the inverted index for the search engine.
- **`italy_city_restaurant_map.html`**: General map of restaurant locations.
- **`links.txt`**: List of Michelin-starred restaurant URLs.
- **`main.ipynb`**: Main notebook with implementations for data collection, search engines, and visualizations.
- **`top_k_restaurant_map.html`**: Highlights top-k restaurants using the custom scoring metric.
- **`vocabulary.csv`**: Vocabulary of unique terms for indexing.

---
