# API Reference

## Overview
This document provides a comprehensive reference for all system components, file formats, and interfaces in the Job Tracker System.

## File Formats

### JSON Configuration Files

#### User Rules (`rules/user-rules.json`)
```json
{
  "meta": {
    "version": "1.0",
    "created": "2024-01-15",
    "description": "User preferences and customization rules",
    "schema_version": "1.0"
  },
  "personal_preferences": { ... },
  "communication_style": { ... },
  "content_preferences": { ... },
  "job_application_strategy": { ... },
  "industry_preferences": { ... },
  "role_preferences": { ... },
  "geographic_preferences": { ... },
  "salary_preferences": { ... },
  "content_customization": { ... },
  "writing_style_preservation": { ... },
  "formatting_preferences": { ... },
  "quality_thresholds": { ... },
  "automation_preferences": { ... },
  "reporting_preferences": { ... }
}
```

#### Meta CV Template (`meta/meta-cv-template.json`)
```json
{
  "meta": { ... },
  "personal_information": { ... },
  "profile": { ... },
  "education": [ ... ],
  "professional_development": [ ... ],
  "work_experience": [ ... ],
  "projects": [ ... ],
  "technical_skills": { ... },
  "soft_skills": [ ... ],
  "languages": [ ... ],
  "achievements_awards": [ ... ],
  "publications": [ ... ],
  "volunteer_experience": [ ... ],
  "interests_activities": [ ... ],
  "references": [ ... ],
  "custom_sections": [ ... ],
  "preferences": { ... }
}
```

#### Meta Cover Letter Template (`meta/meta-cover-letter-template.json`)
```json
{
  "meta": { ... },
  "cover_letter_paragraphs": [ ... ],
  "cover_letter_templates": [ ... ],
  "preferences": { ... }
}
```

### Markdown Files

#### CV Template (`templates/cv-template.md`)
```markdown
# CV Template

## Personal Information
**Name**: [Your Full Name]
**Phone**: [Your Phone Number]
**Email**: [Your Email Address]
...

## Profile
[Professional summary]

## Education
**[Degree Type] in [Subject]**, [University Name]
...
```

#### Personal Statement Template (`templates/personal-statement-template.md`)
```markdown
# Personal Statement Template

[Content based on selected structure approach]

---
*Personal statement for [Job Title] at [Company Name]*
```

### CSV Files

#### Tracker (`tracker.csv`)
```csv
ID,Job Position,Company,Max. Salary,Location,Status,Date Saved,Deadline,Date Applied,Follow up,Excitement
JOB_20240115_001,Data Scientist,TechCorp,120000,Remote,Applied,2024-01-15,2024-01-30,2024-01-16,Follow up in 1 week,8
```

**Note**: For better CSV viewing and editing experience, install "Edit csv" or "Excel Viewer" extension in VS Code/VS Code Fork. **Edit CSV** is particularly recommended for its advanced CSV editing capabilities.

#### Requirements Template (`templates/requirements-template.csv`)
```csv
Criteria,Required/Desired,CV Evidence,Personal Statement Evidence,Strength Level,Score (1-10),How to Improve,Notes,Action Items
Python programming,Required,work_001,technical_001,Strong,9,Continue building projects,Core skill,Maintain proficiency
```

## Data Structures

### Metadata Schema
```json
{
  "display_priority": 1,
  "searchable": true,
  "relevance_score": 0.9,
  "keywords": ["keyword1", "keyword2"],
  "target_audience": "technical",
  "industry": "technology",
  "privacy_level": "public"
}
```

### Content Item Schema
```json
{
  "id": "unique_identifier",
  "type": "content_type",
  "content": "actual_content",
  "metadata": { ... }
}
```

### Job Information Schema
```json
{
  "id": "JOB_YYYYMMDD_XXX",
  "job_position": "Job Title",
  "company": "Company Name",
  "location": "Location",
  "url": "Job Posting URL",
  "description": "Full job description",
  "max_salary": "Salary range",
  "status": "Application status",
  "date_saved": "YYYY-MM-DD",
  "deadline": "YYYY-MM-DD",
  "date_applied": "YYYY-MM-DD",
  "follow_up": "Follow-up notes",
  "excitement": "1-10 scale"
}
```

## System Interfaces

### Instruction Files

#### New Job Processing (`instructions/new-job.md`)
**Purpose**: Process new job applications
**Inputs**: Job description text
**Outputs**: Job folder with analysis files
**Dependencies**: 
- `templates/job-info-template.md`
- `templates/requirements-template.csv`
- `meta/meta-cv-example.json`
- `meta/meta-cover-letter-example.json`

#### CV Generation (`instructions/create-cv.md`)
**Purpose**: Generate targeted CVs
**Inputs**: Job folder, length preference
**Outputs**: `cv.md` file
**Dependencies**:
- `templates/cv-template.md`
- `meta/meta-cv-template.json`
- `meta/meta-cv-example.json`

#### Personal Statement Generation (`instructions/create-personal-statement.md`)
**Purpose**: Generate personal statements
**Inputs**: Job folder, structure approach, length preference
**Outputs**: `personal-statement.md` file
**Dependencies**:
- `templates/personal-statement-template.md`
- `meta/meta-cover-letter-template.json`
- `meta/meta-cover-letter-example.json`

### Content Selection Algorithms

#### Relevance Scoring
```javascript
function calculateRelevanceScore(content, jobRequirements) {
  let score = 0;
  
  // Keyword matching
  score += keywordMatch(content.keywords, jobRequirements.keywords) * 0.4;
  
  // Industry alignment
  score += industryMatch(content.industry, jobRequirements.industry) * 0.3;
  
  // Role alignment
  score += roleMatch(content.target_audience, jobRequirements.role) * 0.2;
  
  // Experience level
  score += experienceMatch(content.experience_level, jobRequirements.level) * 0.1;
  
  return Math.min(score, 1.0);
}
```

#### Content Filtering
```javascript
function filterContent(contentList, filters) {
  return contentList.filter(content => {
    // Quality threshold
    if (content.metadata.relevance_score < filters.minRelevance) return false;
    
    // Target audience
    if (filters.targetAudience && content.metadata.target_audience !== filters.targetAudience) return false;
    
    // Industry
    if (filters.industry && content.metadata.industry !== filters.industry) return false;
    
    // Display priority
    if (content.metadata.display_priority > filters.maxPriority) return false;
    
    return true;
  });
}
```

### File Processing Pipeline

#### Job Processing Pipeline
1. **Input Validation**: Validate job description format
2. **Information Extraction**: Extract company, role, location, salary
3. **Requirements Analysis**: Parse job requirements and skills
4. **Content Mapping**: Map requirements to available content
5. **Folder Creation**: Create job-specific folder structure
6. **File Generation**: Generate analysis and tracking files
7. **Tracker Update**: Update main tracking CSV

#### Content Generation Pipeline
1. **Requirements Loading**: Load job requirements analysis
2. **Content Selection**: Select relevant content based on requirements
3. **Template Application**: Apply selected content to templates
4. **Style Adaptation**: Adapt content to user's writing style
5. **Formatting**: Apply formatting preferences
6. **Quality Check**: Validate content quality and completeness
7. **File Output**: Generate final markdown files

## Configuration Reference

### User Rules Configuration

#### Personal Preferences
```json
"personal_preferences": {
  "name": {
    "value": "string",
    "type": "text",
    "required": true
  },
  "preferred_name": {
    "value": "string",
    "type": "text",
    "required": false
  },
  "professional_title": {
    "value": "string",
    "type": "text",
    "required": false
  }
}
```

#### Communication Style
```json
"communication_style": {
  "tone_preference": {
    "value": "professional|enthusiastic|confident|analytical|creative|authoritative|collaborative",
    "type": "enum",
    "required": true
  },
  "formality_level": {
    "value": "casual|moderate|formal|very_formal",
    "type": "enum",
    "required": true
  },
  "writing_style": {
    "value": "concise|detailed|narrative|technical|conversational",
    "type": "enum",
    "required": true
  }
}
```

#### Content Preferences
```json
"content_preferences": {
  "cv_length_preference": {
    "value": "1_page|2_pages|3_pages|flexible",
    "type": "enum",
    "required": true
  },
  "personal_statement_length": {
    "value": "short|medium|long|flexible",
    "type": "enum",
    "required": true
  }
}
```

### Quality Thresholds
```json
"quality_thresholds": {
  "minimum_relevance_score": {
    "value": 0.6,
    "type": "number",
    "min": 0.0,
    "max": 1.0,
    "required": true
  },
  "minimum_requirement_score": {
    "value": 0.5,
    "type": "number",
    "min": 0.0,
    "max": 1.0,
    "required": true
  }
}
```

## Error Handling

### Common Error Types

#### JSON Validation Errors
```json
{
  "error": "JSON_VALIDATION_ERROR",
  "message": "Invalid JSON format in configuration file",
  "file": "rules/user-rules.json",
  "line": 15,
  "suggestion": "Check JSON syntax and formatting"
}
```

#### File Not Found Errors
```json
{
  "error": "FILE_NOT_FOUND",
  "message": "Required file not found",
  "file": "meta/meta-cv-example.json",
  "suggestion": "Ensure all required files exist in correct locations"
}
```

#### Content Selection Errors
```json
{
  "error": "CONTENT_SELECTION_ERROR",
  "message": "No content found matching requirements",
  "criteria": "Python programming experience",
  "suggestion": "Lower quality thresholds or add more content"
}
```

### Error Recovery
1. **Validation Errors**: Fix JSON syntax and retry
2. **Missing Files**: Create missing files or update paths
3. **Content Errors**: Adjust quality thresholds or add content
4. **Generation Errors**: Check templates and try with defaults

## Performance Considerations

### File Size Limits
- **Meta CV files**: Recommended < 1MB
- **Meta cover letter files**: Recommended < 500KB
- **Job folders**: No specific limit, but consider archiving old jobs
- **Tracker CSV**: Recommended < 10MB

### Processing Time
- **Job processing**: 1-5 seconds per job
- **CV generation**: 2-10 seconds per CV
- **Personal statement generation**: 1-5 seconds per statement
- **Content selection**: < 1 second per selection

### Memory Usage
- **Meta content loading**: ~10-50MB per file
- **Content processing**: ~5-20MB per job
- **Template rendering**: ~1-5MB per document

## Security Considerations

### Data Privacy
- **Personal information**: Store securely, consider encryption
- **Job applications**: Keep confidential, secure access
- **Meta content**: Protect from unauthorized access
- **Tracking data**: Anonymize if sharing

### File Permissions
- **Read access**: Templates, meta content, instructions
- **Write access**: Jobs folder, tracker CSV, user rules
- **Execute access**: Instruction files (if applicable)

### Backup Recommendations
- **Regular backups**: Daily backups of configuration files
- **Version control**: Track changes to important files
- **Archive old jobs**: Move completed applications to archive
- **Test restores**: Regularly test backup restoration

## Reporting System

### Report Types

#### New Job Analysis Report
- **Filename**: `new-job-analysis-{job_id}-{timestamp}.md`
- **Content**: Job match analysis, requirement scoring, action items
- **Technical Details**: Processing steps, data sources, validation results
- **Quality Metrics**: Data completeness, accuracy scores, validation results

#### CV Generation Report
- **Filename**: `cv-generation-{job_id}-{timestamp}.md`
- **Content**: Content selection rationale, template customization, quality metrics
- **Technical Details**: Source files, processing steps, customization details
- **Quality Metrics**: Content relevance scores, completeness assessment

#### Personal Statement Generation Report
- **Filename**: `personal-statement-generation-{job_id}-{timestamp}.md`
- **Content**: Structure selection, content choices, writing style application
- **Technical Details**: Source files, processing steps, structure approach
- **Quality Metrics**: Content relevance scores, completeness assessment

#### Meta Update Report
- **Filename**: `meta-update-{timestamp}.md`
- **Content**: New/updated entries, data quality metrics, writing style analysis
- **Technical Details**: Processing steps, validation results, quality scores
- **Quality Metrics**: Completeness scores, accuracy assessments

### Report Configuration

#### Reporting Preferences Schema
```json
"reporting_preferences": {
  "save_reports": {
    "value": true,
    "type": "boolean",
    "required": true,
    "metadata": {
      "display_priority": 1,
      "searchable": true,
      "description": "Save detailed reports to reports/ folder"
    }
  },
  "report_format": {
    "value": "markdown",
    "type": "enum",
    "options": ["markdown", "json", "both"],
    "required": true,
    "metadata": {
      "display_priority": 2,
      "searchable": true,
      "description": "Format for saved reports"
    }
  },
  "include_timestamps": {
    "value": true,
    "type": "boolean",
    "required": true,
    "metadata": {
      "display_priority": 3,
      "searchable": true,
      "description": "Include timestamps in report filenames"
    }
  },
  "report_retention_days": {
    "value": 30,
    "type": "integer",
    "required": true,
    "metadata": {
      "display_priority": 4,
      "searchable": true,
      "description": "Number of days to keep reports before cleanup"
    }
  },
  "detailed_analysis": {
    "value": true,
    "type": "boolean",
    "required": true,
    "metadata": {
      "display_priority": 5,
      "searchable": true,
      "description": "Include detailed analysis in reports"
    }
  },
  "include_metadata": {
    "value": false,
    "type": "boolean",
    "required": true,
    "metadata": {
      "display_priority": 6,
      "searchable": true,
      "description": "Include metadata and technical details in reports"
    }
  }
}
```

### Report Generation Logic

#### Conditional Reporting
- **Reports only generated if `save_reports` is true**
- **Timestamps only added if `include_timestamps` is true**
- **Detailed analysis only included if `detailed_analysis` is true**
- **Metadata only included if `include_metadata` is true**
- **JSON reports only generated if `report_format` is "json" or "both"**

#### Report Content Structure
- **Executive Summary**: High-level overview of results
- **Analysis Results**: Detailed findings and scores
- **Technical Details**: Processing steps and validation results
- **Quality Metrics**: Scores and assessments
- **Recommendations**: Action items and next steps
- **Metadata**: System information and processing details

## Integration Points

### External Systems
- **Job boards**: Import job descriptions
- **ATS systems**: Export formatted applications
- **Email systems**: Send applications and follow-ups
- **Calendar systems**: Schedule interviews and follow-ups

### API Endpoints (Future)
- **Job processing**: POST /api/jobs
- **Content generation**: POST /api/generate/cv
- **Status updates**: PUT /api/jobs/{id}/status
- **Analytics**: GET /api/analytics

### Data Export
- **CSV export**: Export tracking data
- **PDF generation**: Convert markdown to PDF
- **Email integration**: Send applications via email
- **Cloud storage**: Sync with cloud storage services
