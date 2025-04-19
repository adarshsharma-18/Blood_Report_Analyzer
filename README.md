# CrewAI Health Assistant

> **Note:** This is the description of the assignment, refer to CONFIG.md for installing dependencies and LLMs for the assignment, refer to ACKNOWLEDGMENT.md for my acknowledgments 😊

## Description

This project sets up a crew of agents using the CrewAI framework to create a health assistant. The health assistant takes a sample blood test report, analyzes it, searches the internet for articles tailored to the person's health needs based on the blood test results, and finally provides health recommendations along with relevant article links.

## Approach

1. **Framework Selection**: Utilize the CrewAI framework for building the health assistant.
2. **Data Input**: Develop a module to take input in the form of a sample blood test report.
3. **Data Analysis**: Analyze the blood test report to extract relevant health information.
4. **Web Scraping**: Implement web scraping functionality to search the internet for articles related to the person's health needs.
5. **Recommendations**: Generate health recommendations based on the analyzed data and the retrieved articles.

## Code Description

This project contains 2 agents specialized in different tasks:

### Expert Blood Analyser

- **Role**: Expert Blood Analyser
- **Backstory**: Expert in blood report analysis. Decades of experience in providing comprehensive reports on blood tests. Determines whether blood values are within normal ranges and provides tailored health recommendations.
- **Goal**: Summarize the blood report, identifying normal and abnormal values. Provide health recommendations and links to articles for each abnormality found.

### Text Summarisation Expert

- **Role**: Text Summarisation Expert
- **Backstory**: Skilled in summarizing text and extracting essential details. Proficient at condensing information into concise formats.
- **Goal**: Extract relevant information from the text related to blood analysis and summarize it in a brief format for the user.

## Installation Guide

### Setting up Ollama with Deepseek

1. **Install Ollama**:
   - Download Ollama from [ollama.ai](https://ollama.ai)
   - Follow the installation instructions for your operating system
   - Verify installation by running `ollama --version` in terminal

2. **Pull Deepseek Model**:
   ```bash
   ollama pull deepseek-r1
   ```

3. **Create Deepseek Environment**:
   ```bash
   python -m venv deepseek_env
   source deepseek_env/bin/activate  # On Unix/macOS
   .\deepseek_env\Scripts\activate  # On Windows
   ```

4. **Install Required Dependencies**:
   ```bash
   pip install crewai langchain ollama
   ```

5. **Configure Environment**:
   - Create a `.env` file in project root
   - Add the following configuration:
     ```env
     OLLAMA_BASE_URL="http://localhost:11434"
     MODEL_NAME="deepseek-coder"
     ```

## IMPORTANT POINTS

1. **CrewAI Usage and Cost**: CrewAI is well suited for OpenAI, specifically ChatGPT-3.5-Turbo and ChatGPT-4. However, it requires payment for each request made, potentially leading to high costs.

2. **Local LLM Performance**: Deepseek-coder from Ollama provides excellent performance for code-related tasks and is free to use locally.

3. **Performance Comparison**: While OpenAI models may provide better performance, local LLMs like Deepseek offer a cost-effective alternative with good results.

4. **Compatibility with Text and PDFs**: The assignment works well with text and PDFs containing tables as blood reports, particularly on the first page. The code is designed to check only the first page, but it can be easily modified to check all pages using loops.

5. **Troubleshooting**:
   - Ensure Ollama service is running before starting the application
   - Check port 11434 is available for Ollama
   - Verify environment activation before running the application

## How to Run

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/adarshsharma-18/Blood_Report_Analyzer
   cd Blood_Report_Analyzer-main
   ```

2. **Follow Installation Guide**:
   - Complete all steps in the Installation Guide section above
   - Ensure Ollama is running and Deepseek model is pulled

3. **Prepare Your Blood Report**:
   - Place your blood report PDF in the project root directory
   - Note: The report should be in PDF format with tables

4. **Run the Application**:
   ```bash
   # Activate your virtual environment
   .\deepseek_env\Scripts\activate  # On Windows
   source deepseek_env/bin/activate  # On Unix/macOS

   # Run the main script
   python main.py
   ```

5. **View Results**:
   - The analysis results will be displayed in the terminal
   - A detailed report will be saved in OUTPUT.md
