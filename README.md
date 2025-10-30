# ScholarAI - Meta Repository

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

The main repository containing all ScholarAI components as Git submodules. This repository serves as the central hub for the entire ScholarAI ecosystem - a comprehensive research assistant platform powered by AI.

## 🏗️ Architecture Overview

ScholarAI is a distributed microservices application with AI-powered agents for academic research assistance. The platform enables researchers to search papers, extract insights, analyze research gaps, and manage their research workflow.

```
ScholarAI/
├── Frontend/                    # Next.js web application
├── Microservices/              # Spring Boot microservices
│   ├── service_registry        # Eureka service discovery
│   ├── api_gateway            # Spring Cloud Gateway
│   ├── user_service           # User auth & profiles
│   ├── notification_service   # Email notifications
│   └── project_service        # Research project management
├── AI-Agents/                 # Python FastAPI AI services
│   ├── paper-search           # Academic paper search
│   ├── extractor              # PDF content extraction
│   └── gap-analyzer           # Research gap analysis
├── Docker/                    # Docker compose configurations
└── Scripts/                   # Deployment scripts
```

## 🚀 Quick Start

### Prerequisites

- **Git** 2.13+ (with submodule support)
- **Docker** 20.10+ and Docker Compose
- **Node.js** 18+ (for frontend development)
- **Java** 21+ (for microservices development)
- **Python** 3.11+ (for AI agents development)

### Clone with Submodules

```bash
# Clone the repository with all submodules
git clone --recursive https://github.com/ScholarAI-Echologyx-Hackathon-2025/meta.git

# Or if already cloned, initialize submodules
git submodule update --init --recursive
```

### Environment Setup

1. Copy environment templates:
```bash
cp env.example .env
cp Docker/env.example Docker/.env
```

2. Configure environment variables in `.env` files for:
   - Database credentials
   - API keys (OpenAI, Semantic Scholar, etc.)
   - Service URLs
   - Email/SMTP settings

### Running the Application

#### Development Mode (All Services)

```bash
# Start all services with Docker Compose
cd Docker
docker-compose -f services.yml up -d
```

#### Production Mode

```bash
# Start production services
cd Docker
docker-compose -f services-prod.yml up -d
```

#### Individual Services

Each submodule can be run independently. See their respective README files:

- [Frontend Documentation](./Frontend/README.md)
- [Service Registry](./Microservices/service_registry/README.md)
- [API Gateway](./Microservices/api_gateway/README.md)
- [User Service](./Microservices/user_service/README.md)
- [Notification Service](./Microservices/notification_service/README.md)
- [Project Service](./Microservices/project_service/README.md)
- [Paper Search Agent](./AI-Agents/paper-search/README.md)
- [Extractor Agent](./AI-Agents/extractor/README.md)
- [Gap Analyzer Agent](./AI-Agents/gap-analyzer/README.md)

## 📦 Components

### Frontend (Next.js + TypeScript)

Modern web application built with:
- Next.js 14 with App Router
- TypeScript for type safety
- Tailwind CSS for styling
- shadcn/ui components
- Real-time chat interface

**Features:**
- User authentication (email/password, Google, GitHub)
- Research paper search and analysis
- AI-powered chat assistant
- Research gap analysis
- Document library management
- Project organization

### Microservices (Spring Boot + Java 21)

#### Service Registry (Eureka)
- Service discovery and registration
- Health monitoring
- Load balancing support

#### API Gateway (Spring Cloud Gateway)
- Centralized routing
- Request/response logging
- CORS configuration
- Rate limiting
- Authentication filter

#### User Service
- User authentication & authorization
- JWT token management
- Social OAuth (Google, GitHub)
- User profile management
- Password reset & email verification
- Login rate limiting

#### Notification Service
- Email notifications via SMTP
- Template-based emails (Thymeleaf)
- RabbitMQ integration
- Retry logic with exponential backoff

#### Project Service
- Research project management
- Paper organization
- Collaboration features
- Version control for research

### AI Agents (Python + FastAPI)

#### Paper Search
- Semantic Scholar API integration
- Advanced search queries
- Citation network analysis
- Result ranking and filtering

#### Extractor
- Multi-method PDF extraction
- GROBID for structure
- Table Transformer for tables
- OCR support (Tesseract)
- Figure and equation extraction
- 95%+ extraction coverage

#### Gap Analyzer
- Research gap identification
- Literature review automation
- Trend analysis
- Recommendation generation

## 🛠️ Development

### Updating Submodules

```bash
# Update all submodules to latest
git submodule update --remote --merge

# Update specific submodule
cd Microservices/user_service
git pull origin main
```

### Working with Submodules

```bash
# Make changes in a submodule
cd Frontend
# ... make your changes ...
git add .
git commit -m "Your changes"
git push

# Update parent repo to track new commit
cd ..
git add Frontend
git commit -m "Update Frontend submodule"
git push
```

### Running Tests

```bash
# Frontend tests
cd Frontend && npm test

# Java microservices tests
cd Microservices/user_service && ./mvnw test

# Python AI agents tests
cd AI-Agents/extractor && pytest
```

## 🌐 Service Endpoints

When running locally with default configuration:

| Service | URL | Description |
|---------|-----|-------------|
| Frontend | http://localhost:3000 | Web application |
| API Gateway | http://localhost:8989 | API entry point |
| Service Registry | http://localhost:8761 | Eureka dashboard |
| User Service | http://localhost:8081 | User management |
| Notification Service | http://localhost:8082 | Email service |
| Project Service | http://localhost:8083 | Projects API |
| Paper Search | http://localhost:8001 | Search API |
| Extractor | http://localhost:8002 | Extraction API |
| Gap Analyzer | http://localhost:8003 | Analysis API |

## 🔒 Security

- JWT-based authentication
- Password encryption (BCrypt)
- Rate limiting on login attempts
- CORS configuration
- Secure cookie handling
- Input validation
- SQL injection prevention

## 📊 Monitoring & Observability

- Spring Boot Actuator for health checks
- Request logging in API Gateway
- Service registry dashboard
- Application metrics
- Error tracking and logging

## 🚢 Deployment

### GitHub Actions CI/CD

Automated deployment workflows for all services:
- `.github/workflows/deploy-frontend.yml`
- `.github/workflows/deploy-user-service.yml`
- `.github/workflows/deploy-notification-service.yml`
- `.github/workflows/deploy-api-gateway.yml`
- `.github/workflows/deploy-service-registry.yml`
- `.github/workflows/deploy-project-service.yml`
- `.github/workflows/deploy-paper-search.yml`
- `.github/workflows/deploy-extractor.yml`
- `.github/workflows/deploy-gap-analyzer.yml`
- `.github/workflows/deploy-infra.yml`

### Manual Deployment

```bash
# Deploy with scripts
./Scripts/docker.sh up      # Development
./Scripts/local.sh start    # Local testing
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make changes in the appropriate submodule
4. Commit changes to submodule
5. Update parent repo to reference new commit
6. Create pull request

## 📝 License

This project is licensed under the MIT License.

## 👥 Team

ScholarAI Echologyx Team - Hackathon 2025

## 🆘 Support

For issues and questions:
- Check individual service README files
- Open an issue in the relevant repository
- Contact the development team

## 🎯 Roadmap

- [ ] Enhanced AI chat capabilities
- [ ] Real-time collaboration features
- [ ] Advanced citation management
- [ ] Mobile application
- [ ] Kubernetes deployment
- [ ] Enhanced analytics dashboard
- [ ] API rate limiting and quotas
- [ ] Multi-language support

## 📚 Documentation

Detailed documentation for each component:
- [Frontend Guide](./Frontend/README.md)
- [Microservices Architecture](./Microservices/README.md)
- [AI Agents Overview](./AI-Agents/README.md)
- [Deployment Guide](./docs/DEPLOYMENT.md)
- [API Documentation](./docs/API.md)

---

**Built with ❤️ by the ScholarAI Team**
