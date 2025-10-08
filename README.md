# Primal Employee Monorepo

A comprehensive employee management platform with interactive dashboards, development tools, and AI-powered features. This repository aggregates multiple projects via Git submodules.

## Repository Structure

```
Primal-employee/
├── primal-user-view/          # Main Next.js app (submodule)
├── third_party/              # External templates & examples
├── vercel-ai-chatbot/        # Reference AI chatbot (submodule)
└── README.md                 # This file
```

## Projects Overview

### 1. Primal User View (Main App)
- **Location**: `primal-user-view/`
- **Tech**: Next.js 15, React 19, TypeScript, Tailwind CSS
- **Features**:
  - Interactive Sphere of Influence (React Flow)
  - Development dashboard with calendar & 1:1 meetings
  - Mood & stress tracking with charts
  - Manager notes with weekly intervals

### 2. Third Party Examples
- **Location**: `third_party/`
- **Purpose**: Reference implementations and templates
- **Includes**: Hume EVI starter, UI components

### 3. Vercel AI Chatbot
- **Location**: `vercel-ai-chatbot/`
- **Purpose**: Reference AI chatbot implementation
- **Tech**: Next.js, AI SDK, Drizzle ORM

## Getting Started

### Prerequisites
- Node.js 18+ 
- npm or yarn
- Git

### 1. Clone the Repository
```bash
git clone https://github.com/Pranoy-dev/Primal-employee.git
cd Primal-employee
```

### 2. Initialize Submodules
```bash
# Initialize and update all submodules
git submodule update --init --recursive

# Or clone with submodules in one command
git clone --recurse-submodules https://github.com/Pranoy-dev/Primal-employee.git
```

### 3. Set Up Main Application
```bash
cd primal-user-view
npm install
npm run dev
```

Open `http://localhost:3000` to see the application.

### 4. Environment Variables (Optional)
Create `.env.local` in `primal-user-view/` for AI features:
```bash
# Only needed for embedded AI chatbot features
OPENAI_API_KEY=your_openai_api_key
```

## Implementation Guide

### Adding New Features

#### 1. Sphere of Influence Customization
Edit `primal-user-view/components/sphere-floating/initial-elements.ts`:

```typescript
// Add new employee node
{
  id: "new-employee",
  position: { x: 400, y: 200 },
  data: { label: "John Doe", role: "Product Manager" },
  style: {
    background: "linear-gradient(135deg, #color1, #color2)",
    color: "white",
    border: "2px solid #border-color",
    borderRadius: "12px",
    padding: "12px 16px",
    fontSize: "14px",
    fontWeight: "600",
  }
}

// Add connection
{ id: "e-you-new", source: "you", target: "new-employee", type: "animated" }
```

#### 2. Adding New Dashboard Pages
1. Create page in `primal-user-view/app/dashboard/[page-name]/page.tsx`
2. Add navigation link in `primal-user-view/components/app-sidebar.tsx`
3. Follow the card pattern from existing pages

#### 3. Adding Development Tools
1. Create component in `primal-user-view/components/`
2. Add route in `primal-user-view/app/development/[slug]/page.tsx`
3. Update navigation in `DevHeaderNav` function

### Working with Submodules

#### Making Changes
```bash
# 1. Work inside the submodule
cd primal-user-view
# Make your changes
git add .
git commit -m "feat: add new feature"
git push origin main

# 2. Update parent repository
cd ..
git add primal-user-view
git commit -m "update: sync primal-user-view submodule"
git push origin main
```

#### Updating Submodules
```bash
# Update all submodules to latest
git submodule update --remote

# Update specific submodule
git submodule update --remote primal-user-view
```

#### Cloning for New Developers
```bash
# Clone with all submodules
git clone --recurse-submodules https://github.com/Pranoy-dev/Primal-employee.git

# Or if already cloned
git submodule update --init --recursive
```

## Deployment

### Main Application
The `primal-user-view/` app can be deployed to:
- **Vercel** (recommended): Connect GitHub repo, auto-deploy from `primal-user-view/` folder
- **Netlify**: Build command `cd primal-user-view && npm run build`
- **Railway/Render**: Set root directory to `primal-user-view/`

### Environment Variables for Production
Set these in your deployment platform:
```bash
OPENAI_API_KEY=your_production_key  # If using AI features
NEXT_PUBLIC_APP_URL=https://your-domain.com
```

## Development Workflow

### 1. Feature Development
```bash
# Create feature branch in main repo
git checkout -b feature/new-dashboard

# Work in submodule
cd primal-user-view
git checkout -b feature/new-dashboard
# Make changes
git add . && git commit -m "feat: implement new dashboard"
git push origin feature/new-dashboard

# Update parent repo
cd ..
git add primal-user-view
git commit -m "update: sync new dashboard feature"
git push origin feature/new-dashboard
```

### 2. Code Quality
```bash
cd primal-user-view
npm run build  # Check for build errors
npm run lint   # If lint script exists
```

### 3. Testing
```bash
cd primal-user-view
npm run dev    # Test locally
# Visit http://localhost:3000/dashboard/sphere-of-influence
# Visit http://localhost:3000/development/one-on-one
```

## Troubleshooting

### Submodule Issues
```bash
# If submodule is out of sync
git submodule update --init --recursive --force

# If you see "detached HEAD" in submodule
cd primal-user-view
git checkout main
```

### Build Issues
```bash
# Clear node_modules and reinstall
cd primal-user-view
rm -rf node_modules package-lock.json
npm install
```

### Port Conflicts
```bash
# Run on different port
cd primal-user-view
npm run dev -- -p 3001
```

## Contributing

1. Fork the repository
2. Clone with submodules: `git clone --recurse-submodules [your-fork]`
3. Create feature branch
4. Make changes in appropriate submodule
5. Test thoroughly
6. Submit pull request

## Documentation
- **Main App**: `primal-user-view/README.md` — detailed routes, components, customization
- **AI Chatbot**: `vercel-ai-chatbot/README.md` — reference implementation
- **Third Party**: `third_party/*/README.md` — individual project docs

## Support
- Create issues in the main repository
- Check existing documentation in submodule READMEs
- Review commit history for implementation examples