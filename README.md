# Virtual Teaching Assistant API

This project implements a Virtual Teaching Assistant API that can be customized for any course. The API intelligently responds to student queries by leveraging your course materials and historical discussions, providing quick, accurate, and automated support for learners.

## Features

- ✅ **FastAPI REST endpoint** at `/api/` accepting POST requests
- ✅ **JSON request/response format** with question and optional base64 image
- ✅ **Structured response** with detailed answers and relevant links
- ✅ **Course content integration** - easily add your own course materials
- ✅ **Discussion forum integration** - connect to your preferred forum platform
- ✅ **Customizable knowledge base** - adapt to any subject or course

## Setup

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Set up environment variables:
```bash
cp .env.example .env
# Edit .env with your configuration
```

3. Add your course content:
   - Place your course materials in `data/course_content.json`
   - Add forum discussions in `data/discourse_posts.json`
   - Or use the scraper to collect data automatically

4. Run the application:
```bash
python app.py
```

## API Usage

### Endpoint
POST `/api/`

### Request Format
```json
{
  "question": "Your question here",
  "image": "base64_encoded_image_data_optional"
}
```

### Response Format
```json
{
  "answer": "Detailed answer to the question",
  "links": [
    {
      "url": "URL to relevant resource",
      "text": "Resource description"
    }
  ]
}
```

### Example Usage
```bash
curl "http://localhost:8000/api/" \
  -H "Content-Type: application/json" \
  -d '{"question": "What are the course prerequisites?"}'
```

## Project Structure

```
├── app.py                 # Main FastAPI application
├── scraper/
│   └── scraper.py        # Content and forum scraper
├── data/
│   ├── discourse_posts.json # Forum discussions data
│   └── course_content.json  # Course materials data
├── models/
│   ├── request_models.py    # API request models
│   └── response_models.py   # API response models
├── services/
│   ├── question_processor.py # Question analysis
│   └── answer_generator.py   # Answer generation logic
├── requirements.txt       # Python dependencies
├── LICENSE               # MIT License
└── README.md            # Project documentation
```

## Customization

1. **Course Content**: Update `data/course_content.json` with your course materials
2. **Forum Integration**: Modify `scraper/scraper.py` to work with your forum
3. **Answer Generation**: Customize `services/answer_generator.py` for your needs
4. **Question Processing**: Adjust `services/question_processor.py` for your domain

## Testing

To test the application:

1. Update `project-tds-virtual-ta-promptfoo.yaml` with your test cases
2. Run: `npx -y promptfoo eval --config project-tds-virtual-ta-promptfoo.yaml`

## License

MIT License - see LICENSE file for details.
