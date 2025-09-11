# Complete User Guide

## Table of Contents
1. [Getting Started](#getting-started)
2. [System Setup](#system-setup)
3. [Processing Jobs](#processing-jobs)
4. [Generating Applications](#generating-applications)
5. [Updating Meta Content](#updating-meta-content)
6. [Customizing Content](#customizing-content)
7. [Managing Applications](#managing-applications)
8. [Reporting System](#reporting-system)
9. [Advanced Features](#advanced-features)
10. [Troubleshooting](#troubleshooting)

## Getting Started

### What is the Job Tracker System?
The Job Tracker System is an intelligent job application management tool that:
- Analyzes job descriptions and extracts requirements
- Generates targeted CVs and personal statements
- Tracks application progress and follow-ups
- Preserves your authentic writing style
- Customizes content for specific roles and companies

### Key Benefits
- **Time Saving**: Automatically generate tailored applications
- **Consistency**: Maintain professional quality across all applications
- **Personalization**: Preserve your unique voice and style
- **Organization**: Track all applications in one place
- **Intelligence**: Match content to job requirements automatically

## System Setup

### Step 1: Configure User Rules
1. **Copy the default rules**:
   ```bash
   cp rules/rules-default.json rules/user-rules.json
   ```

2. **Edit your personal information**:
   ```json
   "personal_preferences": {
     "name": {
       "value": "Your Full Name"
     },
     "preferred_name": {
       "value": "Your Preferred Name"
     },
     "professional_title": {
       "value": "Your Professional Title"
     }
   }
   ```

3. **Customize communication style**:
   ```json
   "communication_style": {
     "tone_preference": "professional",
     "formality_level": "moderate",
     "writing_style": "concise"
   }
   ```

4. **Set content preferences**:
   ```json
   "content_preferences": {
     "cv_length_preference": "2_pages",
     "personal_statement_length": "medium",
     "include_photo": false,
     "include_references": false
   }
   ```

### Step 2: Set Up Meta Content
1. **Create your meta CV**:
   - Copy `templates/meta-cv-template.json` to `meta/my-meta-cv.json`
   - Populate with your personal information, experience, and skills
   - Use the example file as a reference

2. **Create your meta cover letter**:
   - Copy `templates/meta-cover-letter-template.json` to `meta/my-meta-cover-letter.json`
   - Add various paragraph types for different situations
   - Customize content for your industry and experience level

3. **Install CSV viewer extension** (recommended):
   - Install "Edit csv" or "Excel Viewer" extension in VS Code/VS Code Fork
   - **Edit CSV** is particularly recommended for its advanced CSV editing capabilities
   - This makes it much easier to view and edit CSV files like `tracker.csv` and `requirements.csv`

### Step 3: Test the System
1. **Process a sample job**:
   - Find a job description online
   - Use the new job processing instructions
   - Review the generated analysis

2. **Generate sample content**:
   - Create a CV using the generated requirements
   - Generate a personal statement
   - Review and adjust your rules if needed

## Processing Jobs

### Using the New Job Instructions
When you find a job you want to apply for:

1. **Provide the job description** to the agent
2. **Reference the instructions**: `@instructions/new-job.md`
3. **Specify any customizations** (e.g., CV length, personal statement approach)

### What Happens Automatically
1. **Job folder creation**: `jobs/JOB_YYYYMMDD_XXX/`
2. **Job information extraction**: Company, role, location, salary
3. **Requirements analysis**: Skills, qualifications, experience needed
4. **CV evidence mapping**: Links your qualifications to job requirements
5. **Personal statement evidence mapping**: Identifies relevant content
6. **Analysis report**: Recommendations and gap analysis
7. **Tracker update**: Adds entry to main tracking CSV

### Understanding the Output
Each job folder contains:
- `job-info.md`: Complete job details and tracking
- `requirements.csv`: Detailed requirements analysis
- `analysis-report.md`: Strategic recommendations

## Generating Applications

### Creating a CV
1. **Reference the CV instructions**: `@instructions/create-cv.md`
2. **Specify the job folder**: `jobs/JOB_YYYYMMDD_XXX/`
3. **Set length preference**: 1 page, 2 pages, 3 pages, or flexible
4. **Review the generated CV**: `jobs/JOB_YYYYMMDD_XXX/cv.md`

### Creating a Personal Statement
1. **Reference the personal statement instructions**: `@instructions/create-personal-statement.md`
2. **Specify the job folder**: `jobs/JOB_YYYYMMDD_XXX/`
3. **Choose structure approach**: Default, story-first, achievement-first, or company-first
4. **Set length preference**: Short, medium, long, or flexible
5. **Review the generated statement**: `jobs/JOB_YYYYMMDD_XXX/personal-statement.md`

### Structure Approaches Explained
- **Default Skeleton**: Introduction → Experience → Skills → Achievement → Company → Closing
- **Story-First**: Opening Story → Experience → Skills → Achievement → Company Alignment → Closing
- **Achievement-First**: Opening Impact → Experience → Skills → Additional Achievements → Company Value → Closing
- **Company-First**: Company Mission → Personal Connection → Experience → Skills → Achievement → Closing

## Updating Meta Content

### What are Meta Documents?
Meta documents are your content libraries that store:
- **Meta CV**: All your professional information, experiences, skills, and achievements
- **Meta Cover Letter**: Reusable paragraphs for different types of applications

### When to Update Meta Content
- **New job or promotion**: Add new work experience
- **New skills or certifications**: Update technical skills
- **New projects or achievements**: Add significant accomplishments
- **Career changes**: Update focus areas and interests
- **Regular maintenance**: Keep content current and relevant

### How to Update Meta Content
1. **Reference the update instructions**: `@instructions/update-meta.md`
2. **Provide new data**: CV, personal statement, or raw text
3. **Specify update type**: New entries, updates to existing, or both
4. **Review the changes**: Check generated report for accuracy

### Types of Updates
- **New CV entries**: Add new work experience, projects, skills, certifications
- **Updated CV entries**: Modify existing entries with new information
- **New cover letter paragraphs**: Add new reusable content
- **Updated paragraphs**: Modify existing paragraphs with new details

### Data Sources
- **Linked CV**: Provide URL or file path to existing CV
- **Personal statement**: Submit written personal statement
- **Raw text**: Provide unstructured information to be categorized
- **User input**: Direct text input with context

## Customizing Content

### Writing Style Preservation
The system automatically preserves your authentic writing style through:
- **Voice consistency**: Maintains your natural tone throughout
- **Sentence structure**: Preserves your preferred sentence patterns
- **Vocabulary choices**: Uses your preferred terminology
- **Personal expressions**: Keeps your unique phrasing

### Content Customization Options
1. **Always include sections**: Force inclusion of specific content
2. **Never include sections**: Exclude certain content types
3. **Custom phrases**: Replace common phrases with your preferences
4. **Avoid words**: Exclude specific words or terms

### Industry and Role Targeting
1. **Set target industries**: Define your preferred industries with scores
2. **Specify target roles**: List roles you're interested in
3. **Avoid certain areas**: Exclude industries or roles you don't want
4. **Geographic preferences**: Set location preferences and exclusions

## Managing Applications

### Tracking Progress
The main `tracker.csv` file contains:
- Job ID, position, company, location
- Salary information and status
- Application dates and deadlines
- Follow-up notes and excitement level

**Tip**: Install a CSV table viewer extension (like "Edit csv" or "Excel Viewer") in VS Code/VS Code Fork to view and edit the tracker in a more user-friendly table format. **Edit CSV** is particularly recommended for its advanced CSV editing capabilities.

### Status Management
- **Saved**: Job saved but not yet applied
- **Applied**: Application submitted
- **Interview**: Interview scheduled or completed
- **Rejected**: Application rejected
- **Offer**: Job offer received
- **Withdrawn**: Application withdrawn

### Follow-up Management
- Set follow-up dates and actions
- Track response rates and outcomes
- Monitor application patterns
- Identify successful strategies

## Reporting System

### Overview
The system automatically generates detailed reports for all major operations, providing insights into:
- **Content quality**: How well your content matches job requirements
- **System performance**: Processing times and validation results
- **Writing style preservation**: How well your voice is maintained
- **Content selection**: Why specific content was chosen

### Report Types
- **New Job Analysis**: Detailed analysis of job match and requirements
- **CV Generation**: Content selection rationale and customization details
- **Personal Statement Generation**: Structure selection and content choices
- **Meta Updates**: Summary of content library updates and improvements

### Configuring Reports
Control report generation through your user rules:
```json
"reporting_preferences": {
  "save_reports": true,
  "report_format": "markdown",
  "include_timestamps": true,
  "report_retention_days": 30,
  "detailed_analysis": true,
  "include_metadata": false
}
```

### Report Settings
- **Save Reports**: Enable/disable automatic report generation
- **Report Format**: Choose markdown, JSON, or both formats
- **Include Timestamps**: Add timestamps to report filenames
- **Retention Days**: How long to keep reports (default: 30 days)
- **Detailed Analysis**: Include comprehensive analysis and metrics
- **Include Metadata**: Include technical details and processing information

### Report Location
All reports are saved to the `reports/` folder with descriptive filenames:
- `new-job-analysis-{job_id}-{timestamp}.md`
- `cv-generation-{job_id}-{timestamp}.md`
- `personal-statement-generation-{job_id}-{timestamp}.md`
- `meta-update-{timestamp}.md`

### Using Reports
- **Review Quality**: Check content quality scores and recommendations
- **Track Progress**: Monitor improvements over time
- **Identify Patterns**: Find successful content combinations
- **Debug Issues**: Use technical details to troubleshoot problems
- **Optimize Content**: Use insights to improve your meta content

## Advanced Features

### Quality Thresholds
Control content quality through:
- **Minimum relevance score**: Only include highly relevant content
- **Minimum requirement score**: Only address requirements above threshold
- **Custom scoring**: Adjust scores based on your preferences

### Automation Preferences
Configure automatic generation:
- **Auto-generate CV**: Automatically create CVs for new jobs
- **Auto-generate personal statement**: Automatically create personal statements
- **Auto-update tracker**: Automatically update tracking information
- **Require approval**: Review before generating content

### Specialized Preferences
For advanced users:
- **Technical focus**: Emphasize specific technical areas
- **Achievement style**: Control how achievements are presented
- **Company research depth**: Set depth of company research
- **Custom formatting**: Define specific formatting preferences

## Troubleshooting

### Common Issues

#### Content Not Generated
- **Check quality thresholds**: Lower minimum scores if needed
- **Verify meta content**: Ensure meta CV/cover letter files exist
- **Review job requirements**: Check if requirements are too specific
- **Validate JSON**: Ensure all configuration files are valid JSON

#### Wrong Tone or Style
- **Adjust communication style**: Change tone preference in rules
- **Modify writing style**: Update writing style preference
- **Check custom phrases**: Review phrase replacements
- **Update voice preservation**: Adjust voice consistency settings

#### Missing Content
- **Check include/exclude settings**: Review always/never include sections
- **Verify relevance scores**: Ensure content meets minimum thresholds
- **Update meta content**: Add missing content to meta files
- **Adjust job requirements**: Check if requirements are too restrictive

#### Formatting Issues
- **Check formatting preferences**: Review date format, bullet style, headers
- **Validate markdown**: Ensure generated content is valid markdown
- **Review template structure**: Check if template structure is correct
- **Update section headers**: Verify header formatting preferences

### Getting Help

#### Self-Help Steps
1. **Check documentation**: Review relevant documentation sections
2. **Validate configuration**: Ensure all JSON files are valid
3. **Test with defaults**: Try with default settings first
4. **Review examples**: Compare with example files

#### Debugging Process
1. **Start simple**: Use minimal configuration first
2. **Test incrementally**: Add complexity gradually
3. **Check logs**: Review any error messages or warnings
4. **Validate output**: Ensure generated content meets expectations

#### Best Practices
1. **Regular backups**: Keep copies of working configurations
2. **Version control**: Track changes to configuration files
3. **Testing**: Test with sample jobs before real applications
4. **Documentation**: Keep notes on successful configurations

### Performance Optimization

#### File Management
- **Regular cleanup**: Remove old job folders periodically
- **Archive completed**: Move completed applications to archive
- **Optimize meta content**: Keep meta files focused and relevant
- **Update regularly**: Refresh content based on new experience

#### Content Quality
- **Review and update**: Regularly update meta content
- **Refine rules**: Adjust rules based on application success
- **Monitor patterns**: Track what works for different job types
- **Iterate and improve**: Continuously refine the system

## Next Steps

### Expanding the System
1. **Add more meta content**: Expand your content libraries
2. **Create industry-specific rules**: Develop specialized configurations
3. **Build application templates**: Create templates for different job types
4. **Integrate with job boards**: Connect with external job sources

### Advanced Customization
1. **Custom scoring algorithms**: Develop specialized relevance scoring
2. **Industry-specific templates**: Create templates for your industry
3. **Automated follow-ups**: Set up automated follow-up systems
4. **Analytics and reporting**: Track application success patterns

### Continuous Improvement
1. **Monitor success rates**: Track which applications get responses
2. **Refine content selection**: Improve content selection algorithms
3. **Update preferences**: Adjust rules based on experience
4. **Expand capabilities**: Add new features and functionality
