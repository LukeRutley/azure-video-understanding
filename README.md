# Azure Video Understanding with OpenAI

A Python notebook demonstrating how to analyze video content using Azure OpenAI's GPT-4.1 vision capabilities. This approach provides greater control over frame extraction rate, resolution, and analysis workflow compared to Azure's pre-built video content understanding service.

## Why This Project?

While Azure offers a [built-in video content understanding solution](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/video/overview), it has technical constraints:

- **Frame sampling (~1 FPS):** Inspects about one frame per second, potentially missing rapid motions
- **Frame resolution (512 × 512 px):** Resized frames may lose small text or distant objects

This notebook overcomes these limitations by providing:
- ✅ Customizable frame extraction rates
- ✅ Full resolution frame processing
- ✅ Complete control over the analysis workflow
- ✅ Cost transparency and optimization

## Features

- Extract frames from video files at any desired rate
- Process frames with Azure OpenAI GPT-4.1
- Calculate processing costs with detailed breakdown
- Support for various video formats
- Optimized for cost efficiency with configurable detail levels

## 📋 Prerequisites

### Azure Resources
- Azure OpenAI resource with GPT-4.1 deployed

## 🛠️ Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/lukerutley/azure-video-understanding.git
   cd azure-video-understanding
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables:**
   ```bash
   export AZURE_OPENAI_ENDPOINT="https://your-resource.openai.azure.com/"
   ```

4. **Authenticate with Azure:**
   ```bash
   az login
   ```

## 📚 Usage

### Basic Usage

1. Place your video file in the project directory (or update the path in the notebook)
2. Open the Jupyter notebook:
   ```bash
   jupyter notebook video-understanding.ipynb
   ```
3. Run all cells to process your video

### Customization Options

**Frame Extraction Rate:**
```python
target_fps = 1  # Extract 1 frame per second
target_fps = 0.5  # Extract 1 frame every 2 seconds
target_fps = 2  # Extract 2 frames per second
```

**Image Detail Level:**
```python
detail = "low"   # Faster, cheaper processing
detail = "high"  # More detailed analysis, higher cost
```

**Custom Analysis Prompts:**
```python
# Modify the prompt in the notebook for specific use cases
"content": [
    {
        "type": "text",
        "text": "Analyze these video frames for security incidents and unusual activities."
    },
    # ... frames
]
```

## 💰 Cost Analysis

The notebook automatically calculates processing costs based on current Azure OpenAI pricing:

- **Input tokens**: $2.00 per million tokens
- **Output tokens**: $8.00 per million tokens

**Example Calculation:**  
For a 30-second video clip sampled at 1 frame per second (30 frames), with each image using approximately 170 tokens:

- **Input tokens:** 170 tokens/frame × 30 frames = 5,100 tokens
- **Output tokens:** (example) 300 tokens total

**Cost Breakdown:**
```
Token Usage:
    Input tokens: 5,100
    Output tokens: 300
    Total tokens: 5,400

Cost Breakdown:
    Input cost: $0.0102
    Output cost: $0.0024
    Total cost: $0.0126
```

## 🎬 Use Cases

- **Security & Surveillance**: Analyze security footage for incidents
- **Insurance Claims**: Process dash cam footage for auto insurance
- **Content Moderation**: Review video content for compliance
- **Research**: Analyze behavioral patterns in video data
- **Quality Assurance**: Monitor manufacturing processes
- **Sports Analysis**: Break down athletic performance


## 🔧 Performance Tips

1. **Cost Optimization:**
   - Use `detail="low"` for general analysis
   - Use `detail="high"` only when fine details are crucial
   - Adjust frame sampling rate based on video content

2. **Quality Optimization:**
   - Higher frame rates for action-heavy content
   - Lower frame rates for static or slow-moving content
   - Experiment with different prompts for specific use cases

3. **Processing Efficiency:**
   - Process shorter video segments for testing
   - Use structured outputs for automated workflows
   - Batch similar videos for consistent analysis


## 📚 Additional Resources

- [Azure OpenAI Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/)
- [Azure OpenAI Pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/)
- [OpenCV Python Documentation](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)
- [Azure Identity Documentation](https://learn.microsoft.com/en-us/python/api/overview/azure/identity-readme)
