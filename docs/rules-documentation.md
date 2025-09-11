# User Rules and Preferences Documentation

## Overview
The user rules system allows for comprehensive customization of job application generation. Users can define their preferences for tone, content, formatting, and automation to ensure all generated CVs and personal statements align with their personal style and career goals.

## File Structure
```
rules/
├── user-rules-example.json    # Example user preferences
└── rules-documentation.md     # This documentation

templates/
└── rules-template.json        # Template for creating new rules
```

## Getting Started

### 1. Create Your Rules File
1. Copy `templates/rules-template.json` to `rules/user-rules.json`
2. Customize the values according to your preferences
3. Save the file in the `rules/` directory

### 2. Reference in Instructions
When using the instruction files, reference your rules file:
```
@rules/user-rules.json
```

## Configuration Sections

### Personal Preferences
- **Name**: Your full name and preferred name
- **Professional Title**: Your current or target professional title
- **Contact Information**: Basic personal details

### Communication Style
- **Tone Preference**: Professional, enthusiastic, confident, analytical, creative, authoritative, collaborative
- **Formality Level**: Casual, moderate, formal, very formal
- **Writing Style**: Concise, detailed, narrative, technical, conversational
- **Voice Preferences**: First person usage, active voice preference

### Content Preferences
- **CV Length**: 1 page, 2 pages, 3 pages, or flexible
- **Personal Statement Length**: Short, medium, long, or flexible
- **Include/Exclude Sections**: Photo, references, interests, volunteer work, publications

### Job Application Strategy
- **Default Structure Approach**: Default skeleton, story-first, achievement-first, company-first, or auto-select
- **Content Emphasis**: Quantified results, job-specific keywords, cultural fit
- **Skill Gap Handling**: Minimize, acknowledge, address directly, or ignore

### Industry and Role Preferences
- **Target Industries**: List with preference scores (0.0-1.0)
- **Avoid Industries**: Industries to exclude with reasons
- **Target Roles**: Specific roles with preference scores
- **Avoid Roles**: Roles to exclude with reasons

### Geographic Preferences
- **Preferred Locations**: Locations with preference scores
- **Avoid Locations**: Locations to exclude with reasons

### Salary Preferences
- **Minimum Salary**: Lowest acceptable salary
- **Target Salary**: Desired salary range
- **Salary Flexibility**: Rigid, moderate, flexible, or negotiable

### Content Customization
- **Always Include Sections**: Sections that must appear in every application
- **Never Include Sections**: Sections to exclude from all applications
- **Custom Phrases**: Preferred alternatives to common phrases
- **Avoid Words**: Words to avoid in all communications

### Formatting Preferences
- **Date Format**: MM/YYYY, Month YYYY, YYYY-MM, MM/DD/YYYY
- **Bullet Style**: Dash, bullet, number, or arrow
- **Section Headers**: Title case, upper case, lower case, or sentence case

### Quality Thresholds
- **Minimum Relevance Score**: Lowest score for including content (0.0-1.0)
- **Minimum Requirement Score**: Lowest score for addressing job requirements (0.0-1.0)

### Automation Preferences
- **Auto Generate CV**: Automatically create CV when processing new jobs
- **Auto Generate Personal Statement**: Automatically create personal statement
- **Auto Update Tracker**: Automatically update tracker CSV
- **Require Approval**: Require user approval before generating content

## Advanced Customization

### Specialized Preferences
For users with specific needs, additional sections can be added:

```json
"specialized_preferences": {
  "technical_focus": {
    "emphasize_ml_algorithms": true,
    "emphasize_data_engineering": true,
    "emphasize_cloud_platforms": true
  },
  "achievement_style": {
    "prefer_quantified_results": true,
    "include_business_impact": true,
    "show_technical_complexity": true
  },
  "company_research_depth": {
    "level": "detailed",
    "include_mission_values": true,
    "include_recent_news": true
  }
}
```

## Usage Examples

### Example 1: Technical Professional
```json
{
  "communication_style": {
    "tone_preference": "analytical",
    "formality_level": "moderate",
    "writing_style": "technical"
  },
  "job_application_strategy": {
    "default_structure_approach": "achievement_first",
    "emphasize_quantified_results": true
  }
}
```

### Example 2: Creative Professional
```json
{
  "communication_style": {
    "tone_preference": "creative",
    "formality_level": "casual",
    "writing_style": "narrative"
  },
  "job_application_strategy": {
    "default_structure_approach": "story_first",
    "show_cultural_fit": true
  }
}
```

### Example 3: Leadership Professional
```json
{
  "communication_style": {
    "tone_preference": "authoritative",
    "formality_level": "formal",
    "writing_style": "detailed"
  },
  "job_application_strategy": {
    "default_structure_approach": "company_first",
    "emphasize_quantified_results": true
  }
}
```

## Integration with Instructions

### In New Job Processing
The `new-job.md` instructions can reference user rules to:
- Set default preferences for new job applications
- Apply user-specific content selection criteria
- Use preferred tone and formatting

### In CV Generation
The `create-cv.md` instructions can use rules to:
- Apply preferred CV length and structure
- Include/exclude sections based on user preferences
- Use preferred formatting and terminology

### In Personal Statement Generation
The `create-personal-statement.md` instructions can use rules to:
- Select appropriate structure approach
- Apply preferred tone and writing style
- Use custom phrases and avoid specified words

## Best Practices

### 1. Start Simple
Begin with basic preferences and add complexity over time.

### 2. Test and Iterate
Generate a few applications and refine your rules based on results.

### 3. Be Specific
The more specific your preferences, the better the generated content.

### 4. Regular Updates
Update your rules as your career goals and preferences evolve.

### 5. Version Control
Keep track of changes to your rules file for reference.

## Troubleshooting

### Common Issues
1. **Rules not being applied**: Ensure the rules file is in the correct location and properly formatted
2. **Conflicting preferences**: Check for contradictory settings in different sections
3. **Missing content**: Verify that quality thresholds aren't too high
4. **Wrong tone**: Adjust communication style preferences

### Validation
Use JSON validators to ensure your rules file is properly formatted:
- Online JSON validators
- VS Code JSON validation
- Command line tools

## Migration and Updates

### Updating Rules
1. Make changes to your `user-rules.json` file
2. Test with a sample job application
3. Adjust as needed
4. Save and use for future applications

### Backing Up Rules
1. Keep a backup of your working rules file
2. Document major changes
3. Test changes before applying to all applications

## Support

For questions or issues with the rules system:
1. Check this documentation
2. Review the example file
3. Validate your JSON format
4. Test with simple preferences first
