# Deepseek_Local_Deployment
DeepSeek R1 (1.5b) model (or its distilled variant by changing version) Deployment using Ollama’s API

# DeepSeek Local Deployment with Ollama
## Technical Documentation

### Prerequisites
- Python 3.7+
- Ollama installed on your system
- Requests library (`pip install requests`)
- Minimum 8GB RAM
- NVIDIA GPU (optional but recommended)

### Installation Steps

1. **Install Ollama**
   ```bash
   # macOS
   brew install ollama

   # Linux
   curl -fsSL https://ollama.ai/install.sh | sh

   # Windows (PowerShell)
   iwr -useb https://ollama.ai/install.ps1 | iex
   ```

2. **Pull DeepSeek Model**
   ```bash
   ollama pull deepseek-r1:1.5b
   ```

### Code Structure Explanation

#### 1. API Configuration
- The code uses Ollama's local API endpoint (`http://localhost:11434/api/chat`)
- Communication happens via HTTP POST requests
- JSON is used for data exchange

#### 2. Main Function: deepseek_query
- **Purpose**: Handles communication with the local DeepSeek model
- **Parameters**:
  - `model_name`: Specifies the DeepSeek model version
  - `prompt`: Input text for the model
  - `stream`: Toggle for streaming responses
- **Return Value**: Model's response as a string
- **Error Handling**: Raises exceptions for non-200 status codes

#### 3. Implementation Details
- Uses the requests library for HTTP communication
- Implements proper error handling and response parsing
- Supports both streaming and non-streaming responses
- Maintains a simple, reusable interface

### Usage Examples

1. **Basic Query**
   ```python
   response = deepseek_query("deepseek-r1:1.5b", "What is machine learning?")
   print(response)
   ```

2. **With Streaming**
   ```python
   response = deepseek_query("deepseek-r1:1.5b", "Explain neural networks", stream=True)
   print(response)
   ```

### Performance Considerations
- Local inference speed depends on hardware capabilities
- GPU acceleration automatically used if available
- Memory usage scales with model size and input length

### Troubleshooting
1. Check if Ollama is running (`ollama list`)
2. Verify model is downloaded (`ollama pull deepseek-r1:1.5b`)
3. Ensure port 11434 is not blocked
4. Check system resources (RAM, CPU usage)

### Maintenance and Updates
- Keep Ollama updated (`brew upgrade ollama` on macOS)
- Monitor the DeepSeek GitHub repository for model updates
- Check API compatibility when updating dependencies
