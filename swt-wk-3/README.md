# 🧑‍💻 Week 3 Lab: Setting Up SonarQube for Static Code Analysis

## 🎯 Learning Objectives

By the end of this lab, you will be able to:

- Install and set up SonarQube (or SonarCloud)
- Create a SonarQube project and run a static analysis scan on a sample project
- Analyze and interpret the results of a SonarQube report
- Reflect on how automated static analysis complements manual code reviews

---

## 📋 What You'll Need

- SonarQube installed locally **or** SonarCloud (free tier) set up
- SonarLint extension installed in VS Code (optional)
- The `Calculator.html` file (download or clone the repository)

---

## 🧪 What You'll Do

### 1. Install SonarQube Locally or Set Up SonarCloud

#### **Option 1: Set Up SonarQube Locally**

- Download and unzip SonarQube from the [official site](https://www.sonarqube.org/downloads/)
- Follow the [SonarQube installation guide](https://docs.sonarqube.org/latest/setup/install-server/) for your operating system
- Once installed, open your browser and go to **http://localhost:9000** to access the SonarQube dashboard

**Default login credentials:**  
- **Username:** `admin`  
- **Password:** `admin`

#### **Option 2: Set Up SonarCloud**

- Go to [SonarCloud](https://sonarcloud.io/) and create an account if you don’t have one
- Link your GitHub repository to SonarCloud (if you don’t have one, create a test repository)
- Once linked, create a new project in SonarCloud. SonarCloud will guide you through setting up SonarScanner to analyze your code

---

### 2. Set Up SonarQube for the Calculator Project

#### **Create the Project**

- Clone or download the `Calculator.html` file. This is your JavaScript calculator that you’ll analyze.

#### **Configure SonarQube for Analysis**

- Create a `sonar-project.properties` file in the project folder and add the following configuration:

```properties
sonar.projectKey=calculator-js-project
sonar.projectName=Calculator JS Project
sonar.projectVersion=1.0
sonar.sources=.
sonar.language=js
sonar.sourceEncoding=UTF-8
```

> This tells SonarQube to analyze the JavaScript code embedded in the `Calculator.html` file.

---

### 3. Run the SonarQube Analysis

- Install SonarScanner by following the [SonarScanner installation guide](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/)
- Open your terminal or command prompt and navigate to the folder containing `Calculator.html`
- Run the following command to start the analysis:

```bash
sonar-scanner
```

> This sends your project’s code to SonarQube (or SonarCloud) for inspection.

---

### 4. Review the Results in SonarQube

- After the analysis completes, open your browser and go to:
  - **http://localhost:9000** (for local SonarQube), or
  - Your SonarCloud project URL
- Find the **Calculator JS Project** and click on it to view the analysis results

You should see insights such as:

- **Code Smells**: Suggestions to improve maintainability
- **Bugs**: Functional errors that may cause incorrect behavior
- **Vulnerabilities**: Potential security risks
- **Test Coverage**: (If applicable) metrics on how much code is tested

---

### 5. Analyze and Reflect on the Results

#### **Analyze the Report**

Review the SonarQube report and identify:

- Are there any code smells, bugs, or vulnerabilities detected?
- What specific improvements does SonarQube suggest (e.g., refactoring, security fixes)?

#### **Personal reflection on the Process**

- How did SonarQube help uncover issues you might have missed during manual review?
- What did you learn from the automated analysis?
- Do you agree with SonarQube’s findings? Why or why not?

---

## 📝 What You Need to Practice

- **Screenshot**: A screenshot of your SonarQube or SonarCloud dashboard showing the analysis of your **Calculator JS Project**
- **Issue Summary**: A brief summary of **at least 3 issues** detected (e.g., bugs, code smells, security vulnerabilities)
- **Reflection**: Answer the following:
  - What did you find useful about using SonarQube?
  - How does automated static analysis compare to manual code review in terms of efficiency and depth?

---

## 🧑‍💻 Further Learning

To go deeper with SonarQube:

- Explore **[Quality Gates](https://docs.sonarqube.org/latest/user-guide/quality-gates/)** to enforce code standards before merging
- Learn how to create **custom rules** and quality profiles
- Integrate SonarQube into **CI/CD pipelines** (e.g., GitHub Actions, GitLab CI) for automated analysis on every push

### 🔗 Additional Resources

- [SonarQube Documentation](https://docs.sonarqube.org/)
- [SonarScanner Documentation](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/)
- [SonarCloud Documentation](https://docs.sonarcloud.io/)
- [Understanding Quality Gates](https://docs.sonarqube.org/latest/user-guide/quality-gates/)
