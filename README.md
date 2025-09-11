# Job Tracker System

Copyright (c) 2025 Stable Flow. Licensed under MIT License.

A comprehensive solution for managing job applications, generating targeted CVs and personal statements, and tracking application progress using intelligent content selection and writing style preservation.

## 🚀 Quick Start

1. **Set up your rules**: Copy `rules/rules-default.json` to `rules/user-rules.json` and customize
2. **Create your meta content**: Populate `meta/meta-cv-example.json` and `meta/meta-cover-letter-example.json` with your information
3. **Process a job**: Use the instructions to analyze a job description and generate applications
4. **Track progress**: Monitor applications using `tracker.csv`

## 📁 Project Structure

```
job-tracker/
├── docs/                          # Complete documentation
├── instructions/                  # Agent processing instructions
├── jobs/                          # Individual job application folders
├── meta/                          # Content libraries (CV & cover letters)
├── reports/                       # Detailed operation reports
├── rules/                         # User preferences and customization
├── templates/                     # Base templates and schemas
└── tracker.csv                    # Main job tracking file
```

## 🎯 Key Features

- **Intelligent Content Selection**: AI-powered matching of content to job requirements
- **Writing Style Preservation**: Maintains your authentic voice across all documents
- **Flexible Structure Options**: Multiple CV and personal statement approaches
- **Comprehensive Tracking**: Complete job application lifecycle management
- **Meta Content Management**: Easy updates to your content libraries
- **Detailed Reporting**: Comprehensive reports for all operations
- **Customizable Rules**: Extensive personalization options

## 📚 Documentation

- **[Complete User Guide](docs/user-guide.md)** - Step-by-step instructions
- **[System Overview](docs/system-overview.md)** - Architecture and design
- **[API Reference](docs/api-reference.md)** - Technical specifications
- **[Troubleshooting](docs/troubleshooting.md)** - Common issues and solutions

## 🛠️ Setup

### Prerequisites
- VS Code or VS Code Fork (recommended)
- CSV viewer extension ("Edit csv" or "Excel Viewer")
- JSON editing capabilities

### Initial Configuration
1. Copy `rules/rules-default.json` to `rules/user-rules.json`
2. Customize your personal information and preferences
3. Populate meta content libraries with your information
4. Test with a sample job application

## 📖 Usage

### Processing a New Job
1. Provide job description to the agent
2. Reference `@instructions/new-job.md`
3. System creates job folder with analysis
4. Review requirements analysis and recommendations

### Generating Applications
1. Use `@instructions/create-cv.md` for CV generation
2. Use `@instructions/create-personal-statement.md` for personal statements
3. Content automatically customized for specific job

### Updating Meta Content
1. Use `@instructions/update-meta.md` to update your content libraries
2. Provide new data (CV, personal statement, or raw text)
3. System updates your meta CV and cover letter databases
4. Review generated report for accuracy

### Reviewing Reports
1. Check `reports/` folder for detailed operation reports
2. Review quality metrics and recommendations
3. Use insights to improve your meta content
4. Track system performance over time

## 🔧 Customization

### User Rules
- **Communication Style**: Tone, formality, writing style
- **Content Preferences**: Length, sections, formatting
- **Job Strategy**: Structure approaches, quality thresholds
- **Writing Style Preservation**: Maintain authentic voice

### Meta Content
- **CV Library**: Comprehensive professional information
- **Cover Letter Library**: Paragraph-level content with metadata
- **Rich Metadata**: Searchable, filterable content selection

## 📊 Tracking

The system tracks:
- Job applications and status
- Requirements analysis and scoring
- Follow-up actions and deadlines
- Success patterns and optimization

## 🤝 Contributing

This is a personal job application management system. Feel free to adapt and customize for your needs.

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

---

**Need Help?** Check the [Complete User Guide](docs/user-guide.md) or [Troubleshooting Guide](docs/troubleshooting.md)
