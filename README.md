# Scaffi

**AI-powered scaffolding for programming assignments. Stop staring at specs, start coding.**

Scaffi transforms overwhelming programming assignments into clear, manageable tasks with AI-generated starter code, progressive hints, and instant feedback—helping students learn by doing, not by copying.

### What Scaffi Does

- 📋 **Smart Breakdown** - Parses assignments (PDF or text) into ordered tasks with dependencies
- 🎯 **Starter Code** - Generates scaffolding with TODOs tailored to your experience level (beginner/intermediate/advanced)
- 💡 **Progressive Hints** - Context-aware help that adapts to how many times you've asked
- ⚡ **Live Execution** - Run tests for Python, JavaScript, C#, Java, and more directly in the browser
- 🧪 **Auto-Generated Tests** - Creates test cases from your code to validate solutions
- 🌓 **Modern UI** - Clean interface with dark mode and real-time feedback

## ✨ Key Features

### For Students
- **Assignment Parser** - Upload PDFs or paste text to automatically break down complex assignments
- **Experience-Based Scaffolding** - Generates 5-8 TODOs for beginners, 3-5 for intermediate, 1-3 for advanced
- **Multi-Language Support** - Python, JavaScript, Java, C#, C, C++
- **Live Code Execution** - Run code directly in browser with real-time output (powered by Piston API)
- **Smart Hints** - Progressive help system that gets more specific with each request
- **Test Generation** - Automatically creates test cases from your completed code
- **Concept Examples** - On-demand examples comparing your known language to the target language

### For Learning
- **Template Preservation** - Detects and preserves starter code structure from assignments
- **Multi-File Projects** - Handles complex assignments with multiple files and classes
- **Dependency Tracking** - Shows which tasks depend on others
- **Progress Tracking** - Visual indicators for completed tasks and concepts mastered

## 🛠️ Tech Stack

### Backend
- **FastAPI** - Modern Python web framework
- **Pydantic** - Data validation and settings management
- **Anthropic Claude API** - AI agent for parsing, code generation, and hints
- **Piston API** - Code execution service for running Python, JavaScript, and other languages
- **Uvicorn** - ASGI server
- **pdfplumber** - PDF text extraction

### Frontend
- **React 18** - UI framework
- **TypeScript** - Type safety
- **Vite** - Build tool and dev server
- **React Router** - Client-side routing
- **Monaco Editor** - Code editor (VS Code editor in the browser)
- **Tailwind CSS** - Utility-first CSS framework
- **Zustand** - State management
- **Three.js** - 3D animations

## 📁 Project Structure

```
Scaffi_frontend/
├── backend/                 # Python FastAPI backend
│   ├── agents/             # AI agents for different tasks
│   │   ├── parser_agent.py         # Breaks down assignments
│   │   ├── codegen_agent.py        # Generates starter code
│   │   ├── live_helper.py          # Provides hints
│   │   └── concept_example.py      # Generates concept examples
│   ├── services/           # Core services
│   │   ├── anthropic_client.py     # Claude API client
│   │   ├── code_runner.py          # Code execution service (Piston API)
│   │   └── pdf_extractor.py        # PDF text extraction
│   ├── pyd_models/         # Pydantic schemas
│   │   └── schemas.py              # API request/response models
│   ├── utils/              # Utility functions
│   │   ├── agent_prompts.py        # AI prompts
│   │   └── json_parser.py          # JSON extraction utilities
│   └── main.py             # FastAPI application entry point
│
├── frontend/               # React TypeScript frontend
│   ├── src/
│   │   ├── api/            # API client and endpoints
│   │   ├── components/     # React components
│   │   │   ├── CodeEditor.tsx      # Monaco editor wrapper
│   │   │   ├── ChatBot.tsx         # AI chat interface
│   │   │   ├── PDFUploadZone.tsx   # PDF upload component
│   │   │   └── ui/                 # Reusable UI components
│   │   ├── pages/          # Page components
│   │   │   ├── LandingPage.tsx     # Home page
│   │   │   ├── TaskPage.tsx        # Task breakdown view
│   │   │   └── EditorPage.tsx      # Code editor page
│   │   |── store/          # Zustand state management
│   │   |── types/          # TypeScript type definitions
|   |   |-- lib/
│   └── package.json
│
└── README.md
```

## 🏃 Getting Started

### Prerequisites

- **Python 3.8+** (for backend)
- **Node.js 18+** and **npm** (for frontend - required for React and Vite build tools)
- **Anthropic API Key** - Get one from [Anthropic Console](https://console.anthropic.com/)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Scaffi_frontend
   ```

2. **Set up the backend**
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Set up the frontend**
   ```bash
   cd ../frontend
   npm install
   ```

4. **Configure environment variables**

   Create a `.env` file in the `backend/` directory:
   ```env
   ANTHROPIC_API_KEY=your_anthropic_api_key_here
   ```

   Create a `.env` file in the `frontend/` directory :
   ```env
   VITE_API_BASE_URL=http://127.0.0.1:5000
   ```

### Running the Application

1. **Start the backend server**
   ```bash
   cd backend
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   uvicorn main:app --reload --port 5000
   ```
   The backend will run on `http://127.0.0.1:5000`

2. **Start the frontend development server** (in a new terminal)
   ```bash
   cd frontend
   npm run dev
   ```
   The frontend will run on `http://localhost:5173` (or another port if 5173 is busy)

3. **Open your browser**
   Navigate to `http://localhost:5173` to use the application

## 📡 API Endpoints

### Health Check
- `GET /` - Simple health check
- `GET /health` - Detailed health check with agent status

### Assignment Processing
- `POST /parse-assignment` - Break down assignment into tasks
- `POST /generate-starter-code` - Generate starter code for a task
- `POST /extract-pdf-text` - Extract text from uploaded PDF

### Learning Support
- `POST /get-hint` - Get contextual hint for current task
- `POST /get-concept-example` - Get example of a programming concept

### Code Execution
- `POST /run-code` - Execute Python or JavaScript code (powered by Piston API)

See the FastAPI docs at `http://127.0.0.1:5000/docs` for detailed API documentation.

## 🎯 How It Works

1. **Submit Assignment** - Upload PDF or paste assignment text
2. **AI Analysis** - Claude AI breaks down the assignment into ordered tasks with dependencies
3. **Generate Scaffolding** - Creates starter code with experience-appropriate TODOs for each task
4. **Code in Browser** - Work through tasks in the integrated Monaco editor
5. **Get Help** - Ask for hints that become more detailed with each request
6. **Run & Test** - Execute code instantly and generate test cases to validate your solution
7. **Download** - Export your completed code when done

## 🔧 Development

### Backend Development
```bash
cd backend
source venv/bin/activate
uvicorn main:app --reload --port 5000  # Runs with auto-reload enabled
```

### Frontend Development
```bash
cd frontend
npm run dev     # Development server with hot reload
npm run build   # Production build
npm run preview # Preview production build
```

### Code Style
- Backend: Follow PEP 8 Python style guide
- Frontend: TypeScript with ESLint configuration

## 📝 Environment Variables

### Backend (.env)
- `ANTHROPIC_API_KEY` (required) - Your Anthropic API key for Claude
- `PISTON_API_URL` (optional) - Piston API endpoint, defaults to `https://emkc.org/api/v2/piston`

### Frontend (.env)
- `VITE_API_BASE_URL` (optional) - Backend API URL, defaults to `http://127.0.0.1:8000`

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

MIT License

## �� Acknowledgments

- Built with [Anthropic Claude](https://www.anthropic.com/) for AI capabilities
- Code execution powered by [Piston API](https://emkc.org/) (Engineer Man's Code Execution API)
- UI components inspired by modern design systems
- Code editor powered by [Monaco Editor](https://microsoft.github.io/monaco-editor/)

---

**Made with ❤️ for students learning to code**



---

**Made for students learning to code**
