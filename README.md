# SDN Based DDoS Attack Detection and Mitigation

## Overview

This project implements a DDoS attack detection and mitigation system using Software-Defined Networking (SDN). It leverages machine learning algorithms to identify malicious traffic patterns and employs SDN capabilities to mitigate the attacks in real-time.

## Project Structure

The project is organized into the following directories:
```
├── controller/
│   ├── Temp_files/
│   ├── Collect_benign_tfarric1.py
│   ├── DT_controller.py
│   ├── KNN_controller.py
│   ├── RF_controller.py
│   ├── collect_ddos_trafic.py
│   ├── controller.py
│   ├── mitigation_module.py
│   ├── ML.py
│   ├── start_traffic_collection.py
│   ├── switch.py
│   └── switchm.py
├── mininet/
│   ├── generate_benign_traffic.py
│   ├── generate_ddoc_traffic.py
│   ├── generate_ddoc_traffic1.py
│   └── topology.py
├── mitigation/
│   ├── mitigation_module.py  (Duplicate - Likely should be in controller)
│   └── switchm.py             (Duplicate - Likely should be in controller)
├── ml/
│   ├── DT.py
│   ├── KNN.py
│   ├── LR.py
│   ├── ML.py
│   ├── NB.py
│   ├── RF.py
│   └── SVM.py
├── model/
│   ├── dataset_sdn.csv
│   └── DDoS_Analysis.ipynb
└── README.md
```

**Description of Directories and Files:**

* **`controller/`**: Contains the SDN controller application.
   
* **`mininet/`**: Contains scripts for setting up the Mininet network environment.
 
* **`mitigation/`**: Contains scripts for mitigation module (Mitigation module is only present in KNN_controller.py)
* **`ml/`**: Contains the machine learning model implementations.
    * `DT.py`, `KNN.py`, `LR.py`, `NB.py`, `RF.py`, `SVM.py`:
* **`model/`**: Contains data and analysis related to the machine learning models.
    * `dataset_sdn.csv`: This dataset is only used to figure out which algorithm provides best accuracy and performance, we have generated our own dataset for training purpose.
    * `DDoS_Analysis.ipynb`: Jupyter Notebook used for exploring the dataset, selecting the appropriate machine learning algorithm(s), and evaluating model performance.

## Functionality

The project aims to achieve the following:

1.  **Traffic Generation:** Generate both benign and DDoS attack traffic using Mininet scripts.
2.  **Traffic Collection:** Collect network traffic features from the Mininet environment using the controller.
3.  **DDoS Attack Detection:** Employ machine learning models (Decision Tree, KNN, Random Forest, etc.) within the SDN controller to classify incoming traffic as either benign or malicious.
4.  **Real-time Mitigation:** Upon detecting a DDoS attack, the SDN controller utilizes the `mitigation_module.py` to implement mitigation strategies by manipulating flow rules on the switches.

## Machine Learning Algorithms

The project explores and potentially utilizes the following machine learning algorithms for DDoS detection:

* Decision Tree (DT)
* K-Nearest Neighbors (KNN)
* Logistic Regression (LR)
* Naive Bayes (NB)
* Random Forest (RF) - Provides best efficinecy
* Support Vector Machine (SVM)

The `DDoS_Analysis.ipynb` file  contains the analysis and comparison of these algorithms to determine the most effective one(s) for this specific task.

## Setup and Installation (Example - Adjust as needed)

1.  **Install Mininet:** Follow the instructions on the official Mininet website to install Mininet.
2.  **Install ONOS (or your chosen SDN Controller):** This project seems geared towards an ONOS-like controller structure. Install your preferred SDN controller.
3.  **Clone the Repository:** Clone the repository to your local machine using Git.
4.  **Install Python Libraries:** Ensure you have the necessary Python libraries installed. You can use pip to install them. A `requirements.txt` file would be beneficial to list these dependencies.
    ```bash
    pip install -r requirements.txt
    ```  
5.  **Start the Mininet Topology:** Navigate to the `mininet/` directory and run the `topology.py` script to create the network environment.
    ```bash
    cd mininet/
    sudo python topology.py
    ```
6.  **Start the SDN Controller:** Start your SDN controller application. You might need to configure it to connect to the Mininet switches.
7.  **Run Traffic Generation and Collection:** Execute the scripts in the `mininet/` and `controller/` directories to generate traffic and start the collection process. You might need to adjust the scripts based on your specific controller and setup.
    ```bash
    # Example (adjust as needed)
    python controller/start_traffic_collection.py
    python mininet/generate_benign_traffic.py &
    python mininet/generate_ddoc_traffic.py &
    ```

## Usage

To use this project, follow these steps:
1.  Run the Mininet topology.
2.  Start the SDN controller.
3.  Execute the traffic generation scripts to simulate network traffic, including DDoS attacks.
4.  The controller will collect traffic features and use the trained machine learning model to detect attacks.
5.  Upon detection, the mitigation module in the controller will apply mitigation rules to the switches to block or redirect malicious traffic.

## Potential Improvements and Future Work

* **Enhance Mitigation Strategies:** Implement more sophisticated mitigation techniques beyond basic blocking.
* **Real-time Feature Extraction:** Optimize the traffic feature extraction process for real-time performance.
* **Evaluate Different ML Models:** Thoroughly evaluate the performance of all implemented machine learning models and choose the most suitable one.
* **Implement Feedback Mechanism:** Potentially add a feedback loop to improve the accuracy of the detection model over time.
* **Testing and Evaluation:** Conduct rigorous testing and evaluation of the system's performance under various attack scenarios.
* **Documentation:** Add more detailed documentation for each module and script.
* **GUI or Web Interface:** Develop a user interface for monitoring and managing the system.

## Contributions
    1. Anirudh C M
    2. Chandan T O
    3. Chirag V
    4. Likhith Gowda S R