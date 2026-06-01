# Car Rental Fleet Dataset

This is a dedicated data repository designed to store and serve the initial vehicle dataset and corresponding static image assets for the [Car Rental Management System](https://github.com/Gkhundadze/car-rental-management-system) repository.

The dataset, hosted within this repository, is intended to be fetched and consumed as the initial seed data for the project assignment.

---

## Repository Structure

```directory
car-rental-car-data/
├── README.md              # Project documentation
├── carData.json           # Structured vehicle catalog (JSON format)
└── images/                # High-quality optimized PNG images of fleet models
    ├── audi_etron_gt.png
    ├── bmw_m8_competition.png
    ├── mercedes_g63_amg.png
    ├── porsche_911_gt3.png
    ├── range_rover_autobiography.png
    └── tesla_model_s_plaid.png
```

---

## Dataset Specifications (carData.json)

The dataset contains a structured JSON array of premium car objects. Each vehicle entry is modeled with rich specifications, rental pricing, asset paths, and metadata.

### Data Schema Reference

| Field | Data Type | Description | Example |
| :--- | :--- | :--- | :--- |
| `id` | `string` | Globally unique identifier (UUID v4) | `"b63a7f80-77cb-4b2a-8cbe-d5b76ff3df99"` |
| `brand` | `string` | Manufacturer/make of the vehicle | `"Tesla"` |
| `model` | `string` | Model name of the vehicle | `"Model S Plaid"` |
| `pricePerDay` | `number` | Rental cost per 24-hour period in USD | `180` |
| `image` | `string` | Relative path to the vehicle's image asset | `"images/tesla_model_s_plaid.png"` |
| `transmission`| `string` | Gearbox configuration (Automatic / Manual) | `"Automatic"` |
| `fuel` | `string` | Fuel type (Electric / Petrol / Hybrid / Diesel) | `"Electric"` |
| `seats` | `number` | Passenger seating capacity | `5` |
| `available` | `boolean` | Booking availability status | `true` |
| `featured` | `boolean` | Flag to highlight the car in promotional layouts | `true` |
| `createdAt` | `number` | Unix timestamp (epoch in ms) when recorded | `1717243200000` |

---

## Fleet Directory

Below is the complete list of premium vehicles included in the dataset:

| Brand | Model | Fuel Type | Seats | Price / Day | Status | Featured |
| :--- | :--- | :--- | :---: | :---: | :---: | :---: |
| **Tesla** | Model S Plaid | Electric | 5 | **$180** | Available | Yes |
| **Porsche** | 911 GT3 RS | Petrol | 2 | **$350** | Available | Yes |
| **BMW** | M8 Competition | Petrol | 4 | **$240** | Available | No |
| **Mercedes-Benz** | G 63 AMG | Petrol | 5 | **$290** | Available | Yes |
| **Audi** | e-tron GT | Electric | 5 | **$200** | Available | No |
| **Land Rover** | Range Rover Autobiography | Hybrid | 7 | **$260** | Available | No |

---

## Fetching and Consuming the Data

To populate the main application in the [car-rental-management-system](https://github.com/Gkhundadze/car-rental-management-system) repository, you can fetch `carData.json` directly at runtime.

### Direct API Integration (GitHub CDN)

You can fetch the data file dynamically from the raw GitHub user content URL:

```javascript
const VECHICLE_DATA_URL = 'https://raw.githubusercontent.com/Gkhundadze/car-rental-car-data/main/carData.json';

async function fetchInitialFleet() {
  try {
    const response = await fetch(VECHICLE_DATA_URL);
    if (!response.ok) {
      throw new Error('Failed to load fleet initial data.');
    }
    const vehicles = await response.json();
    return vehicles;
  } catch (error) {
    console.error('Error loading initial fleet data:', error);
  }
}
```

### Resolving Image Assets

The `image` property in the JSON contains the relative path (e.g., `"images/tesla_model_s_plaid.png"`). When rendering these images in your main application, prepend the base raw content URL of this repository to load the images directly:

```javascript
const RAW_ASSETS_BASE_URL = 'https://raw.githubusercontent.com/Gkhundadze/car-rental-car-data/main/';

// Example rendering conversion:
const imageUrl = `${RAW_ASSETS_BASE_URL}${car.image}`;
```

---

## License

This project dataset is open-source and available under the MIT License. Feel free to use it for personal, academic, or commercial portfolios!