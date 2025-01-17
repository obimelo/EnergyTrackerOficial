# Energy Price Tracker for OMIE Market

This repository contains an application for tracking energy prices of the OMIE (Operador del Mercado Ibérico de Energía) market. The application gathers data from the OMIE market and provides a user-friendly interface to visualize and analyze historical energy prices

It also ingest data from E-Redes energy consumption files to analyse the costs of energy using real time and profiled consumption.

A public and free to use site is available at http://energytracker.pt

## Change Log
28/Apr/2023 :
 - Support for different E-Redes Consumer Profiles (BTN A, BTN B, BTN C, IP and UPAC);
 - Resampling of data in "Analysis" to consider 15min, 1 hour, 1 day or 1 week;
 - Performance improvements;
 - Luzboa-Spot fixes;

26/Apr/2023 : 
  - Beta support for Luzboa-Spot;
  - Shows current Cycle day and Supplier on "info" page;
  - Minor layout changes;
  - Bug fixes;

## Table of Contents

1. [Features](#features)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Contributing](#contributing)
6. [License](#license)

## Features

- Retrieve historical and real-time energy prices from the OMIE market
- Visualize data in interactive graphs and charts
- Track energy net prices in real time for a energy supplier
- Analyse energy consumption costs
- Dockerized for easy deployment and scalability

## Prerequisites

Service Backend:
- Docker (>= 20.10)
- Python (>= 3.80)

Frontend:
- Javascript + Bootstrap 5

For more details check requirements.txt file for the service backend

## Installation

1. Clone the repository to your local machine:

```
git clone https://github.com/pedrolsantos/energytracker.git
```

2. Go to folder:
```
cd energyTracker
```

2. Build the Docker container:
```
docker build -t energytracker .
````

3.Start the Docker container:
```
docker run --rm -p 5000:5000 -p 8000:80 energytracker
```

4.Access the application in your browser at http://localhost:8000.

5.Changes to the Frontend:

To make changes to the frontend:

- Install 'google-closure-compiler' (https://github.com/google/closure-compiler) to minimize and optimize the source code
- Compile the app.js using:
```
google-closure-compiler --js app.js --js_output_file app.min.js
```

## Usage

Navigate to the application's main page at `http://localhost:8000`

### *"Info"*
Shows all the information in real time about current OMIE price and Price of the configured energy supplier.
- Real time Prices for OMIE and energy supplier
- Real time energy consumption (if EoT enabled)
- Current period and tariff
- Chart of Net Price for the previous and next 6 hours
- Chart of OMIE Price for the previous and next 6 hours

### *"Analise"*
Provides a tool to ingest excel files from E-Redes user energy consumption (https://balcaodigital.e-redes.pt/consumptions/history) 

Provides information for:
- Real time energy consumption costs and quantities
- Estimated energy consumption costs and quantities based on "Perfil C" of E-Redes: https://www.e-redes.pt/pt-pt/clientes-e-parceiros/comercializadores/perfis-de-consumo

The consumption files from E-Redes must comply with the following rules:
- Have all the information inside "Leituras" sheet
- Have at least the columns:
    - "Data" : consumption date (year/month/day)
    - "Hora" : consumption time (hh:mm)
    - "Consumo registado, Ativa" : energy consumption

### *"Config"*
Provides a set of configuration parameters
- "Horas do Gráfico" : number of hours to be used on the "Info" charts
- "Curva do Perfil C no gráfico" : enable/disable "Perfil C" on top of energy supplier chart
- "Fornecedor" : supplier and plan to use for all calculations
- "Tarifa" : time option of the energy contract
- "Ano" : year to be considered for the calculations
- "Chave EoT:" - EoT key to enable real time display of power and energy consumption (https://www.eot.pt)



## Contributing

We welcome contributions to improve and expand the functionality of the OMIE Energy Price Tracker. To contribute, please follow these steps:

1. Fork the repository and create a new branch for your feature or bugfix.
2. Implement your changes and test them thoroughly.
3. Ensure that your code follows the project's coding standards and guidelines.
4. Submit a pull request to the `main` branch of the original repository.

We will review your submission and provide feedback as soon as possible.

## License

This project is licensed under the MIT License. 
