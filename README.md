# Google-Chronicle-Humio-Package-Integration

This repository contains two python scripts that enable the Chronicle packages in the Humio Marketplace. There are two Chronicle packages in the Humio marketplace, one for alerts and one for IOCs.

The Chronicle alerts package parses and visualizes alert data from the Chronicle Search API. Using this package, you can view Chronicle alerts by hostname, severity, and source. You can also visualize the most recent alerts, file hashes and names associated with alerts, and the event types associated with alerts, such as process starts or network connections.

The Chronicle IOCs package parses and visualizes IOC data from the Chronicle Search API. Using this package, you can view Chronicle IOCs by domain name, severity, source, and category. You can also visualize the most recent IOCs and IOC activity over time.

Each of these python scripts pulls data from their respective Chronicle Search API endpoints at a fixed time interval and posts data recieved to Humio via the HTTP Event Collector (HEC) every 5 minutes. To run either script, you first need to provide your Humio URL, the ingest token for your repository, and the path to your Google Service Account credentials JSON file. You can also configure the polling interval.

```python
HUMIO_INGEST_TOKEN = "YOUR_INGEST_TOKEN_HERE"
HUMIO_BASE_URL = "YOUR_BASE_URL_HERE"
POLLING_INTERVAL = 60 * 5
# Change to the location you placed your JSON file.
SERVICE_ACCOUNT_FILE = "PATH_TO_SERVICE_CREDS_JSON"
```

To run the Chronicle IOCs consumer, run the following command:

```
python3 chronicle_iocs_to_humio.py
```

To run the Chronicle Alerts consumer, run the following command:

```
python3 chronicle_alerts_to_humio.py
```
