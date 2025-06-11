---
publishDate: 2025-05-30T00:40:04-07:00
title: Assignment 3
---

# Deployment and Integration of LLM

**Student Name**: ODAI OTHMAN 

**Student ID**: LS2425241

**Submission Date**: May 30. 2025

**Website URL:** https://odai357.github.io/pehtheme/assignments/assignment3/

---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Environment Setup](#2-environment-setup)
3. [Local Model Deployment with Ollama](#3-local-model-deployment-with-ollama)
4. [DeepSeek Online and Local Comparison](#4-deepseek-online-and-local-comparison)
5. [GUI Integration with AnythingLLM](#5-gui-integration-with-anythingllm)
6. [Development Environment Integration](#6-development-environment-integration)
7. [Performance Comparison](#7-performance-comparison)
8. [Conclusion](#11-conclusion)
9. [Bonus: Research Workflow Optimization](#bonus-research-workflow-optimization-3-points)
10. [Commands Quick Reference](#commands-quick-reference)
11. [Resources](#resources)

---

## 1. Project Overview

This assignment demonstrates the deployment and utilization of both local and online Large Language Models (LLMs). I successfully:
- Deployed a local LLM using Ollama with the DeepSeek-R1 1.5B model
- Configured an online model API (to be implemented)
- Integrated AnythingLLM for a user-friendly GUI interface
- Integrated LLMs into my development workflow

### Why These Tools?
- **Ollama**: Open-source, easy to use, supports multiple models, runs efficiently on local hardware
- **DeepSeek-R1 1.5B**: Lightweight model suitable for my machine's capacity while maintaining good performance
- **AnythingLLM**: Provides professional GUI, supports multiple LLM providers, excellent for productivity

---

## 2. Environment Setup

### System Specifications
- **Operating System**: Windows 11
- **RAM**: [16GB]
- **GPU**: [3060RTX]
- **Storage**: [100GB]
- **Python Version**: 3.10

### Prerequisites
```bash
# Check system requirements
systeminfo

# Ensure adequate storage (minimum 10GB recommended)
# Check GPU availability (optional but recommended)
```

---

## 3. Local Model Deployment with Ollama

### Step 1: Install Ollama

1. **Download Ollama for Windows**:
```bash
# Visit https://ollama.com/download
# Download OllamaSetup.exe
# Run the installer with administrator privileges
```

2. **Verify Installation**:
```bash
ollama --version
# Output: ollama version X.X.X
```

### Step 2: Deploy DeepSeek-R1 Model

1. **Browse Available Models**:
```bash
# Check available models at https://ollama.com/library
ollama list
```

2. **Pull and Run DeepSeek-R1 1.5B**:
```bash
# Download and run the model
ollama run deepseek-r1:1.5b

# This command:
# - Downloads the model if not present
# - Starts an interactive session
# - Shows download progress (1.1GB total)
```

3. **Download Progress**:
![Alt text](/images/565.png)

### Test Local Model
1. **Interactive Testing**:
![Alt text](/images/test.png)



2. **Model Management Commands**:
```bash
# List all installed models
ollama list

# Show model information
ollama show deepseek-r1:1.5b

# Stop a running model
ollama stop deepseek-r1:1.5b

# Remove a model
# ollama rm deepseek-r1:1.5b
```

---

## 5. GUI Integration with AnythingLLM

### Step 1: Install AnythingLLM

1. **Download AnythingLLM**:
```bash
# Visit https://anythingllm.com/download
# Download AnythingLLM-Desktop-Setup.exe
# Install with default settings
```

### Step 2: Configure Ollama Connection

1. **Launch AnythingLLM**
2. **Navigate to LLM Preferences**:
   - Click on "AI Providers" in the left sidebar
   - Select "Ollama" as LLM Provider

3. **Configure Ollama Settings**:
```
Ollama Base URL: http://127.0.0.1:11434
Max Tokens: 4096
Performance Mode: Base (Default)
Ollama Keep Alive: 5 minutes
```

4. **Select Model**:
   - Click on "Ollama Model" dropdown
   - Select "deepseek-r1:1.5b" from available models
   - Models will load after entering a valid Ollama URL

   ![Alt text](/images/66.png)


### Step 3: Test Integration

1. **Create New Workspace**
2. **Test conversation with the integrated model**
3. **Verify responses are coming from local Ollama instance**

---

## 6. Development Environment Integration

### AnythingLLm Integration
![Alt text](/images/123.png)




3. **Usage Examples**:
   - Code completion: Type code and use `Ctrl+I` for suggestions
   - Code explanation: Select code and ask "Explain this code"
   - Refactoring: Select code and ask "Refactor this function"


## 7. DeepSeek Online and Local Comparison

| Feature         | Local (via Ollama)           | Online (via AnythingLLM)     |
|------------------|-------------------------------|-------------------------------|
| Installation     | Required                      | Handled by GUI                |
| Latency          | Very low                      | Slightly higher               |
| Resource Usage   | Uses local GPU/CPU            | Offloaded to API/host system  |
| Internet         | ❌ Not required                | ✅ Required                    |
| Privacy          | ✅ High                        | ⚠️ Depends on host config      |
| Ease of Use      | CLI-based interaction         | Full GUI                      |

Both variants use the same model architecture but differ in delivery: CLI vs GUI/API. I used both modes interchangeably during testing.

---

## 8. GUI Integration with AnythingLLM

- Installed [AnythingLLM](https://anythingllm.com)
- Connected to my local Ollama instance:
  ```
  Base URL: http://127.0.0.1:11434
  Model: deepseek-r1:1.5b
  ```

### Benefits:
- Easier to run conversations
- GUI-based workspace creation and chat history
- Supports multi-model routing

---

## 9. Development Environment Integration

### Using Copilot + DeepSeek

In **Visual Studio Code**, I leveraged:
- **Copilot** for real-time coding suggestions and syntax help
- **DeepSeek (local)** for logic explanation, refactoring, and documentation tasks

### Example Workflow:
1. Write base code with Copilot autocomplete
2. Ask DeepSeek to refactor or optimize code via AnythingLLM
3. Use Copilot again to refine UI logic

---

## 10. Performance Comparison

| Metric              | DeepSeek (Local) | DeepSeek (Online) |
|---------------------|------------------|-------------------|
| Speed               | ✅ Fast           | ⚠️ Slightly slower |
| Stability           | ✅ Reliable       | ✅ Stable          |
| Flexibility         | ✅ Full CLI       | ✅ GUI-based       |
| Usage Mode          | Offline-friendly | Requires internet |
| Cost                | Free             | Free              |

---

## 11. Conclusion

✅ Deployed DeepSeek 1.5B locally  
✅ Connected to AnythingLLM  
✅ Integrated into software development using VS Code and Copilot  
✅ Compared online/local model capabilities  

**Key Learning**:
- DeepSeek models are powerful and usable both locally and through GUI tools like AnythingLLM.
- Combining Copilot for real-time suggestions and DeepSeek for deeper understanding creates an efficient workflow for building software.
### Bonus: Research Workflow Optimization (+3 points)
*I will implement this to devolop a software and add documentation here about integrating LLMs into my research workflow*


---

**Commands Quick Reference**:
```bash
# Ollama commands
ollama run deepseek-r1:1.5b    # Run model
ollama list                     # List models
ollama ps                       # Show running models
ollama stop deepseek-r1:1.5b   # Stop model

# Development integration
code .  # Open VSCode with Continue extension
```

**Resources**:
- [Ollama Documentation](https://github.com/ollama/ollama)
- [DeepSeek Models](https://github.com/deepseek-ai)
- [AnythingLLM Guide](https://docs.anythingllm.com)
- [Continue VSCode Extension](https://continue.dev/docs)