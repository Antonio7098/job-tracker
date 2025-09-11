# Meta CV Template Schema Documentation

## Overview

The Meta CV Template is a comprehensive JSON-based schema designed to store all possible CV information in a structured, searchable format. This template serves as a master database from which targeted CVs can be generated for specific job applications.

## Schema Structure

### Core Principles

1. **Hierarchical Organization**: Information is organized into logical sections
2. **Rich Metadata**: Each entry includes searchable metadata for filtering and relevance scoring
3. **Flexible Content**: Supports various content types and formats
4. **Version Control**: Includes versioning for schema evolution
5. **Privacy Controls**: Different privacy levels for sensitive information

### Main Sections

#### 1. Personal Information (`personal_information`)
- **Basic Info**: Name, preferred name, professional title
- **Contact**: Email, phone, address with privacy controls
- **Online Presence**: LinkedIn, GitHub, portfolio, social media

#### 2. Profile (`profile`)
- **Summary**: Professional summary with character limits
- **Objectives**: Short and long-term career objectives

#### 3. Education (`education`)
- Degree information, institutions, dates, GPA
- Achievements, coursework, relevance scoring
- Support for multiple degrees and certifications

#### 4. Professional Development (`professional_development`)
- Courses, bootcamps, certifications
- Credential tracking with URLs
- Skills gained and industry relevance

#### 5. Work Experience (`work_experience`)
- Detailed job history with achievements
- Technologies used, team size, reporting structure
- Quantified impact and results

#### 6. Projects (`projects`)
- Personal, academic, and professional projects
- Technologies, URLs, team information
- Results and key features

#### 7. Technical Skills (`technical_skills`)
- **Programming Languages**: With proficiency levels and experience
- **Frameworks & Libraries**: Categorized by type
- **Databases**: Database technologies and experience
- **Cloud Platforms**: Cloud services with certifications
- **Tools & Technologies**: DevOps, testing, other tools

#### 8. Soft Skills (`soft_skills`)
- Leadership, communication, problem-solving
- Proficiency levels and descriptions

#### 9. Languages (`languages`)
- Spoken languages with proficiency and certifications
- Relevance scoring for different roles

#### 10. Additional Sections
- **Achievements & Awards**: Professional recognition
- **Publications**: Research papers, articles
- **Volunteer Experience**: Community involvement
- **Interests & Activities**: Personal interests
- **References**: Professional references with privacy controls
- **Custom Sections**: Flexible content areas

## Metadata System

### Core Metadata Fields

Each entry includes these metadata fields:

```json
{
  "display_priority": 1,        // Order of display (1 = highest)
  "searchable": true,           // Whether content is searchable
  "relevance_score": 0.9,       // Relevance score (0.0-1.0)
  "keywords": ["keyword1", "keyword2"], // Search keywords
  "target_audience": "technical", // Target audience type
  "industry": "technology",      // Industry relevance
  "privacy_level": "public"     // Privacy control
}
```

### Audience Types
- `general`: Suitable for all audiences
- `technical`: Technical roles and audiences
- `academic`: Academic and research positions
- `recruiter`: HR and recruitment focused
- `specific`: Highly targeted content

### Industry Categories
- `technology`: Tech industry
- `finance`: Financial services
- `healthcare`: Healthcare and medical
- `education`: Educational institutions
- `government`: Government positions
- `nonprofit`: Non-profit organizations
- `general`: Cross-industry applicable

### Privacy Levels
- `public`: Safe for all audiences
- `private`: Sensitive information
- `confidential`: Highly sensitive

## Usage Patterns

### 1. Job-Specific CV Generation

```json
{
  "filters": {
    "target_audience": "technical",
    "industry": "technology",
    "relevance_score_min": 0.7,
    "display_priority_max": 3
  }
}
```

### 2. Skill-Based Filtering

```json
{
  "skills": {
    "required": ["Python", "Machine Learning"],
    "preferred": ["AWS", "Docker"],
    "exclude": ["PHP", "WordPress"]
  }
}
```

### 3. Experience Level Targeting

```json
{
  "experience": {
    "years_min": 3,
    "years_max": 10,
    "include_entry_level": false
  }
}
```

## Search and Filtering

### Keyword Search
- Full-text search across all searchable fields
- Keyword matching in metadata
- Fuzzy matching for typos

### Relevance Scoring
- Automatic scoring based on job requirements
- Manual override capabilities
- Industry-specific scoring algorithms

### Display Priority
- Controls order of appearance in generated CVs
- Dynamic adjustment based on job requirements
- Fallback ordering for missing priorities

## Best Practices

### 1. Content Guidelines
- Use specific, quantifiable achievements
- Include relevant keywords for your industry
- Maintain consistent formatting and tone
- Regular updates to keep information current

### 2. Metadata Management
- Set appropriate relevance scores
- Use comprehensive keyword lists
- Choose correct target audiences
- Maintain privacy level consistency

### 3. Version Control
- Track changes to the schema
- Maintain backward compatibility
- Document schema evolution

## Integration with CV Template

The meta CV template integrates with the existing `cv-template.md` through:

1. **Content Mapping**: Direct mapping of JSON fields to CV sections
2. **Dynamic Selection**: AI-powered selection of relevant content
3. **Formatting Rules**: Automatic formatting based on content type
4. **Length Control**: Intelligent truncation based on CV length preferences

## Future Enhancements

- **AI Integration**: Machine learning for better content selection
- **Template Variants**: Multiple CV format templates
- **Analytics**: Track which content performs best
- **Collaboration**: Multi-user editing and review
- **Export Formats**: PDF, Word, HTML generation
