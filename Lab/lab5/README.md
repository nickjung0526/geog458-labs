# Lab 5: Millions of Data, Flow Map — San Francisco Bay & Delta Region

## 1. Study Area and Dates
* **Region:** San Francisco Bay, San Pablo Bay, and the Sacramento-San Joaquin River Delta, California (Bounding Box: `[-122.838, 37.408, -120.951, 38.888]`).
* **Dates:** October 13, 2025 (UTC timestamps originating from `2025-10-13T00:00:00+00:00`).
* **Time Zone:** Pacific Daylight Time (PDT, UTC-7) for local display and interpretation.
* **Data Source:** Raw Automatic Identification System (AIS) observation points retrieved from [AccessAIS (MarineCadastre.gov)](https://marinecadastre.gov/accessais/), processed via the class Google Colab notebook into structured vessel trajectory JSON arrays and metadata.
* **Data Management Strategy:** To ensure browser performance and prevent rendering bottlenecks with deck.gl, the spatial request was focused strictly on the Northern California estuary complex rather than the entire Pacific coastline, and restricted to a 3 day time period (October 11, 2025 - October 13, 2025). This yielded a manageable dataset of 1,039 unique vessels and 864,871 output observations.

## 2. Interpretation
* **Temporal Patterns:**
Traffic intensity varies drastically throughout the 24-hour cycle. Passenger vessels and local recreational ferry show high concentrations during 07:00-19:00 PDT. Large commerical cargo ships and tankers demonstrate a continuous movement, navigating shipping lanes regardless of local daylight hours.
* **Route Corridors:** \
Filtered views reveal that cargo vessels and tankers tightly adhere to deep-water navigation channels running from the Golden Gate through San Francisco Bay, past the Richmond-San Rafael Bridge, and into the Port of Oakland or other ports like Stockton and Sacramento. Meanwhile, "other" vessels (fishing, recreational, etc) show dispersed, localized moement clustering near the marinas, yacht harbors, and the bay.
* **Context & Observations:** The observed trajectory concentration in the Carquinez Strait and San Pablo Bay corresponds directly with maritime logistics feeding inland agricultural and industrial terminals. The separation between deep-draft commercial corridors and shallow-draft recreational zones highlights how physical bathymetry constrains digital flow paths. 

## 3. Feature Proposal for a Potential User
* **Target User:** A San Francisco Bay Area Port Authority Marine Operations Planner or Vessel Traffic Service (VTS) coordinator.
* **User Need:** The planner needs to audit historical traffic congestion points and identify specific vessels violating speed restrictions or lingering near sensitive ecological zones or bridge piers during peak operational hours.
* **Proposed Feature:** I propose adding an **Interactive Vessel Inspection Tool / Clickable Tooltip and Metadata Panel** implemented by picking interactions. When a user clicks or hovers over a moving trajectory line on the map, a side panel or floating tooltip would display real-time attributes from the JSON object—such as the vessel's name (`MMSI`), exact length, beam width, current draft, and instantaneous speed over ground (`SOG`) at that specific timestamp.