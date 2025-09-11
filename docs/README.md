# Documentation Index

## Overview
This directory contains comprehensive documentation for the Job Tracker System. The main project README is located in the root directory.

## System Architecture

### Core Components
- **Meta Templates**: JSON-based content libraries for CVs and cover letters
- **Job Processing**: Automated analysis and requirements extraction
- **Content Generation**: AI-powered CV and personal statement creation
- **User Rules**: Customizable preferences and writing style preservation
- **Tracking System**: CSV-based job application management

### File Structure
```
job-tracker/
├── docs/                          # Documentation
│   ├── README.md                  # This file
│   ├── meta-cv-schema.md          # CV template documentation
│   ├── meta-cover-letter-schema.md # Cover letter documentation
│   ├── rules-documentation.md     # User rules guide
│   ├── user-guide.md              # Complete user guide
│   └── api-reference.md           # System API reference
├── instructions/                  # Agent instructions
│   ├── new-job.md                 # New job processing
│   ├── create-cv.md               # CV generation
│   └── create-personal-statement.md # Personal statement generation
├── jobs/                          # Job application folders
│   └── JOB_YYYYMMDD_XXX/          # Individual job folders
├── meta/                          # Meta content libraries
│   ├── meta-cv-example.json       # CV content examples
│   └── meta-cover-letter-example.json # Cover letter examples
├── rules/                         # User preferences
│   ├── rules-default.json         # Default settings
│   ├── user-rules-example.json    # Example configuration
│   └── rules-documentation.md     # Rules guide
├── templates/                     # Base templates
│   ├── cv-template.md             # CV structure template
│   ├── personal-statement-template.md # Personal statement template
│   ├── job-info-template.md       # Job information template
│   ├── requirements-template.csv  # Requirements analysis template
│   ├── meta-cv-template.json      # CV content template
│   ├── meta-cover-letter-template.json # Cover letter template
│   └── rules-template.json        # User rules template
└── tracker.csv                    # Main job tracking file
```

## Quick Start

### 1. Initial Setup
1. Copy `rules/rules-default.json` to `rules/user-rules.json`
2. Customize your personal information and preferences
3. Set up your meta CV and cover letter content

### 2. Processing a New Job
1. Use `instructions/new-job.md` with a job description
2. System creates job folder with analysis
3. Generates requirements analysis and recommendations

### 3. Generating Applications
1. Use `instructions/create-cv.md` for CV generation
2. Use `instructions/create-personal-statement.md` for personal statements
3. Content is automatically customized for the specific job

## Key Features

### Intelligent Content Selection
- **Relevance Scoring**: Content selected based on job requirements
- **Metadata Filtering**: Advanced filtering by industry, role, and preferences
- **Quality Thresholds**: Minimum scores for content inclusion

### Writing Style Preservation
- **Authentic Voice**: Maintains user's natural writing style
- **Smooth Integration**: Seamlessly blends template content with personal voice
- **Consistent Tone**: Ensures uniform voice across all documents

### Flexible Structure Options
- **CV Templates**: Multiple length and format options
- **Personal Statement Approaches**: Story-first, achievement-first, company-first, default
- **Customizable Sections**: Include/exclude based on job requirements

### Comprehensive Tracking
- **Job Management**: Complete job application lifecycle tracking
- **Requirements Analysis**: Detailed analysis of job requirements vs. qualifications
- **Progress Monitoring**: Status tracking and follow-up management

## Documentation Index

### Core Documentation
- **[User Guide](user-guide.md)**: Complete step-by-step user guide
- **[API Reference](api-reference.md)**: System components and interfaces
- **[Meta CV Schema](meta-cv-schema.md)**: CV template structure and usage
- **[Meta Cover Letter Schema](meta-cover-letter-schema.md)**: Cover letter template structure
- **[Rules Documentation](rules-documentation.md)**: User preferences and customization

### Template Documentation
- **[CV Template](templates/cv-template.md)**: CV structure and formatting
- **[Personal Statement Template](templates/personal-statement-template.md)**: Personal statement structure
- **[Job Info Template](templates/job-info-template.md)**: Job information tracking
- **[Requirements Template](templates/requirements-template.csv)**: Requirements analysis format

### Instruction Documentation
- **[New Job Processing](instructions/new-job.md)**: How to process new job applications
- **[CV Generation](instructions/create-cv.md)**: How to generate targeted CVs
- **[Personal Statement Generation](instructions/create-personal-statement.md)**: How to generate personal statements
- **[Update Meta Documents](instructions/update-meta.md)**: How to update meta CV and cover letter databases

## Getting Help

### Common Tasks
1. **Setting up the system**: See [User Guide](user-guide.md)
2. **Customizing preferences**: See [Rules Documentation](rules-documentation.md)
3. **Processing jobs**: See [New Job Processing](instructions/new-job.md)
4. **Generating content**: See [CV Generation](instructions/create-cv.md) and [Personal Statement Generation](instructions/create-personal-statement.md)
5. **Updating meta content**: See [Update Meta Documents](instructions/update-meta.md)

### Troubleshooting
- Check JSON formatting for all configuration files
- Verify file paths and permissions
- Review quality thresholds if content is missing
- Check user rules for conflicting preferences

### Best Practices
- Start with `rules-default.json` and customize gradually
- Test with sample jobs before processing real applications
- Regularly update meta content libraries
- Keep track of successful application patterns
- Review generated reports for insights and improvements

### Reporting System
- **Automatic Reports**: Detailed reports are generated for all major operations
- **Configurable**: Control report generation through user rules
- **Multiple Formats**: Support for markdown and JSON report formats
- **Quality Tracking**: Monitor system performance and content quality
- **Report Location**: All reports saved to `reports/` folder

## System Requirements

### File Formats
- **JSON**: All configuration and meta content files
- **Markdown**: All documentation and generated content
- **CSV**: Job tracking and requirements analysis

### Dependencies
- JSON parser for configuration files
- Markdown processor for content generation
- CSV handler for tracking data

### Recommended Extensions
- **CSV Table Viewer**: For VS Code or VS Code Fork to view and edit CSV files in a table format
  - Install: "Edit csv" or "Excel Viewer" extensions
  - **Edit CSV** is particularly recommended for its advanced CSV editing capabilities
  - Makes it easier to view and edit `tracker.csv` and `requirements.csv` files

### Permissions
- Read access to template and meta files
- Write access to jobs folder and tracker.csv
- Execute permissions for instruction files

## Version Information
- **Current Version**: 1.0
- **Schema Version**: 1.0
- **Last Updated**: 2024-01-15

## Support
For questions or issues:
1. Check the relevant documentation section
2. Review example files for reference
3. Validate JSON formatting
4. Test with minimal configurations first
