# Green-Corridors-Biopoles-for-Carbon-Capture-and-Pollution-Mitigation

import requests
import time
import json
import random

# Constants for the pollution sensors
API_URL = "https://your-cloud-api-endpoint.com/data"  # Replace with your cloud API endpoint
POLLUTANTS = ['PM2.5', 'NO2', 'CO']

# Function to simulate getting data from pollution sensors
def get_pollution_data():
    # Simulate sensor data
    data = {
        'PM2.5': random.uniform(0, 100),  # Replace with actual sensor reading
        'NO2': random.uniform(0, 200),     # Replace with actual sensor reading
        'CO': random.uniform(0, 10)        # Replace with actual sensor reading
    }
    return data

# Function to send data to the cloud
def send_data_to_cloud(data):
    headers = {'Content-Type': 'application/json'}
    response = requests.post(API_URL, headers=headers, data=json.dumps(data))
    
    if response.status_code == 200:
        print("Data sent successfully:", data)
    else:
        print("Failed to send data:", response.status_code, response.text)

# Main function for the IoT application
def main():
    while True:
        pollution_data = get_pollution_data()
        send_data_to_cloud(pollution_data)
        
        # Wait for a specified interval before collecting data again
        time.sleep(60)  # Send data every 60 seconds

if _name_ == "_main_":
    main()
