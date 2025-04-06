## AI-Powered Product Description Generator

### Overview

This project implements an AI-powered product description generator designed to create compelling, SEO-optimized product descriptions and marketing copy from basic product information. The system leverages LLMs to generate missing product fields and product images using available product data.

**Deployment:**

The application has been deployed and is accessible at: https://wilsonz347.github.io/i95dev-technical-assessment/.

### Project 

#### Backend (Python)
- REST API using FastAPI that interfaces with an LLM (OpenAI GPT-3.5-turbo or similar)
- Prompt engineering for the following:
  - Compelling product descriptions
  - SEO-optimized titles and meta descriptions
  - Marketing copy in various formats (email, social media, etc.)
  - Missing product fields (categories, tags, features, etc.)
  - Image descriptions based on product data
  - Product image generation prompts for DALL-E or similar image generation models
- Endpoints for the following:
  - Processing product data and generating content
  - Selecting different content types and formats
  - Customizing tone, length, and style of generated content
  - Generating product images based on product attributes

#### Frontend (React)
- A clean interface for entering product information
- A form with fields for product attributes (name, basic description, price, features, etc.)
- Tabs for different content types (descriptions, marketing copy, SEO elements, image generation)
- A preview and edit functionality for generated content
- A component for visualizing generated image descriptions
- An image generation component that displays generated product images

### Project Structure

#### Backend Structure
```
backend/
│
├── app.py               # Main FastAPI application
├── requirements.txt     # Python dependencies
├── config.py            # Configuration
├── data/
│   └── sample_products.json    # Sample product data
│
├── services/
│   ├── __init__.py
│   ├── llm_service.py   # Service for LLM interactions
│   └── product_service.py  # Service for product data operations
│
└── README.md            # Backend setup instructions
```

#### Frontend Structure
```
frontend/
│
├── public/
│   └── index.html
│
├── src/
│   ├── App.js           # Main application component
│   ├── index.js         # Entry point
│   ├── components/
│   │   ├── ProductForm.js   # Form for product data input 
│   │   ├── ContentType.js   # Content type selector
│   │   ├── GeneratedContent.js  # Display for generated content 
│   │   └── StyleOptions.js  # Style and tone configuration 
│   │
│   ├── services/
│   │   └── api.js       # API client for backend communication
│   │
│   └── styles/
│       └── App.css      # Styling
│
├── package.json         # NPM dependencies
└── README.md            # Frontend setup instructions
```

### Sample Dataset

The sample product dataset (`sample_products.json`) contains 15 products with varying levels of completeness. Some products have missing fields that the system should be able to generate. Each product has the following structure:

```json
{
  "id": "prod123",
  "name": "Ultra-Comfort Running Shoes",
  "price": 89.99,
  "brand": "SportsFlex",
  "basic_description": "Lightweight running shoes with cushioning.",
  "category": "Footwear",
  "subcategory": "Running",
  "features": ["Responsive cushioning", "Breathable mesh"],
  "materials": ["Synthetic mesh", "Rubber outsole"],
  "colors": ["Black/Red", "Blue/White", "Grey/Orange"],
  "tags": ["running", "athletic", "comfortable"],
  "image_url": "https://example.com/images/shoes123.jpg",
  "seo_title": "",
  "seo_description": "",
  "detailed_description": "",
  "marketing_copy": {
    "email": "",
    "social_media": {
      "instagram": "",
      "facebook": ""
    }
  }
}
```

### Key Implementation Guidelines

#### LLM Integration
- OpenAI's API (GPT-3.5-turbo) 
- Proper error handling for API calls
- Appropriate context windows and token limits

#### Prompt Engineering
- Prompts that effectively utilize product attributes to generate compelling content
- Different prompt templates for different content types
- Strategies for maintaining brand voice and style consistency
- Generated content is SEO-friendly for relevant fields
- Effective prompts for generating realistic product images that match product attributes

#### API Design
- RESTful endpoints with proper request/response formats
- Appropriate error handling

#### React Frontend
- Clean, functional UI rather than elaborate designs
- Responsive components that adapt to different screen sizes

### Additional Features
- A ratings system to provide feedback on generated content

### Setup Instructions

#### Backend Setup
1. Navigate to the `backend` directory
2. Create a virtual environment: `python -m venv venv`
3. Activate the virtual environment:
   - Windows: `venv\Scripts\activate`
   - macOS/Linux: `source venv/bin/activate`
4. Install dependencies: `pip install -r requirements.txt`
5. Create a `.env` file based on `.env.example` and add your LLM API key
6. Run the application: `uvicorn app:app --host 0.0.0.0 --port 5000 --reload`

#### Frontend Setup
1. Navigate to the `frontend` directory
2. Install dependencies: `npm install`
3. Start the development server: `npm start`
4. The application should open at `http://localhost:3000`

### Prompt Engineering Approach

My prompt engineering strategy focused on creating efficient and effective prompts to generate high-quality product content. The approach included structured prompt design, precise context injection, and emphasis on SEO best practices, with an iterative refinement process to optimize for the desired output.

- Instead of lengthy, conversational prompts, I utilized concise, well-structured templates. Each prompt was carefully designed to elicit specific content types (descriptions, titles, marketing copy, image prompts) with minimal verbosity. 
- The strategy involved precise mapping of product attributes (name, brand, category, features, materials, etc.) to designated placeholders within the prompt templates.
- Character limits were explicitly enforced within the prompt instructions to ensure that generated content met SEO guidelines.
- To maintain a professional brand voice, the prompt templates incorporated parameters to control the style and tone of the generated content.

### React Frontend Approach

My approach to developing the React frontend involved a structured process of initial assessment, component implementation, state management, and API integration, culminating in the addition of an upvote/downvote system.

- Before writing any code, I carefully reviewed the provided starter kit and the project requirements. I analyzed the existing file structure (App.js, components/, services/api.js) to identify which components needed to be implemented and how they would interact.
- To gather feedback on the generated content, I implemented an upvote/downvote system using React's useState hook to track the number of upvotes and downvotes.

### Technical Challenges
- The starter kit included React components that already fulfilled the project's core UI requirements, leading to initial ambiguity regarding the extent of frontend implementation needed.
- Rate limits imposed by the LLM API restricted the extent of testing and prompt refinement possible within the given timeframe.
- Initial difficulties navigating the starter kit structure and addressing deployment hurdles consumed more time than anticipated.
