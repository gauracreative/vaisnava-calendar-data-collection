# Radhe Radhe!

The JSON data files in this collection are generated from the [Pure Bhakti Vaisnava Calendar](https://www.purebhakti.com/resources/vaisnava-calendar).

If you are developing a calendar app and need the data, rather than scraping it from the website—thus unnecessarily increasing the number of requests (human traffic is most certainly welcome there)—you can fetch the data from this collection.

## Data Structure

### Time Zones

At the root level, you will see folders with names like `N0600`. These represent time zones:
- **"N"** stands for negative (-), i.e., west of Greenwich.
- **"P"** stands for positive (+), i.e., east of Greenwich.

There will also be `zones.json` file with contents similar to the following example:

```json
[
    {
        "title": "+04:00 Abu Dhabi, Tbilisi, Baku",
        "pb": "4",
        "dir": "P0400"
    },
    {
        "title": "+05:00 Chelyabinsk, Ekaterinburg, Ufa",
        "pb": "5",
        "dir": "P0500"
    },
    {
        "title": "+05:30 India",
        "pb": "550",
        "dir": "P0530"
    },
    ...
]

```

In the example above:  

- The `dir` value corresponds to the directory name mentioned earlier.
- The `pb` value represents the option value from the [Pure Bhakti form](https://www.purebhakti.com/resources/vaisnava-calendar).
- The `title` value is the option label displayed on the [Pure Bhakti form](https://www.purebhakti.com/resources/vaisnava-calendar).

### Locations

Inside each time zone folder, you will find a file named `locations.json`. This file contains a JSON array of all locations within that time zone. Here's an example of the data format:

```json
[
  {
    "title": "Austin, Texas, USA",
    "coordinates": "097W41 30N16",
    "timezone": "-6.00",
    "option": "Austin, Texas, USA            097W41 30N16     -6.00",
    "file": "austin_texas_usa_097w41_30n16_6_00"
  },
  {
    "title": "Chicago, Illinois, USA",
    "coordinates": "087W45 41N53",
    "timezone": "-6.00",
    "option": "Chicago, Illinois, USA        087W45 41N53     -6.00",
    "file": "chicago_illinois_usa_087w45_41n53_6_00"
  },
  ...
]

```
- Value of the `option` field above is exactly the value used in the form on [Pure Bhakti](https://www.purebhakti.com/resources/vaisnava-calendar).
- `file` value is the name of the file minus `.json`.

### Location-Specific Files

Within each time zone folder, there are individual JSON files for each location. For example, `N0600/sidney_gopals_texas_usa_098w49_32n01_6_00.json`. These files contain the actual Vaisnava calendar events.

### Sample Event Data Structure

Here's an example of the data structure in a location-specific file:

```json
[
  {
    "date": "2025-02-15",
    "tithi": "Tritīyā",
    "link": "https://www.purebhakti.com/tags/334",
    "events": [
      {
        "title": "+Śrī Śrīmad Bhakti Prajñāna Keśava Gosvāmī Mahārāja ~ Appearance",
        "link": "https://www.purebhakti.com/tags/377,334"
      }
    ]
  },
  {
    "date": "2025-02-17",
    "tithi": "Pañcamī",
    "link": "https://www.purebhakti.com/tags/336",
    "events": [
      {
        "title": "+Jagad-guru Śrī Śrīmad Bhaktisiddhānta Sarasvatī Ṭhākura Prabhupāda ~ Appearance",
        "link": "https://www.purebhakti.com/tags/376,336"
      },
      {
        "title": "+Śrī Śrīmad Bhakti Bhūdeva Śrautī Gosvāmī Mahārāja ~ Appearance",
        "link": ""
      },
      {
        "title": "+Śrīla Gour Govinda Svāmī ~ Disappearance",
        "link": "https://www.purebhakti.com/tags/413,336"
      }
    ]
  },
  ...
]

```

By using this structure, you can easily fetch and utilize data for your calendar application.

As an **example**:

- If you want to fetch all time zones, call `https://vaisnava-calendar-data-collection.gaura.space/N0600/zones.json`.
- If you want to fetch all locations for the `-06:00` time zone, call `https://vaisnava-calendar-data-collection.gaura.space/N0600/locations.json`.
- If you want to get all events for `Sidney, TX` within the zone, call `https://vaisnava-calendar-data-collection.gaura.space/N0600/sidney_gopals_texas_usa_098w49_32n01_6_00.json`.

### Sample App: Automate Event Reminders

If you're looking for a practical way to utilize the data in this collection, check out the [Vaiṣṇava Calendar Reminder App](https://github.com/gauracreative/vcalapp). This sample app makes it easy to send automated reminders for Vaiṣṇava Calendar events directly to Telegram, showcasing how this data can be integrated into your own applications.
