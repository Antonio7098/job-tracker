# New Job Application Processing Instructions

## Overview
This document provides step-by-step instructions for processing a new job application. The agent should follow these instructions when given a job description to create a complete job application package.

## Prerequisites
- **MANDATORY**: Read and load user rules file (`@rules/user-rules.json` or `@rules/rules-default.json`) before starting
- Job description text provided by user
- Access to all template files in the `templates/` directory
- Access to meta CV and cover letter examples
- Write permissions to create new files and folders

## Step-by-Step Process

### Step 1: Create New Job Folder
1. **Generate unique job ID**: Create a unique identifier using format `JOB_YYYYMMDD_XXX` (e.g., `JOB_20240115_001`)
2. **Create folder**: Create a new folder in the `jobs/` directory named with the job ID
3. **Confirm creation**: Verify the folder was created successfully

### Step 2: Create Job Information File
1. **Copy template**: Use `@job-info-template.md` as the base template
2. **Create file**: Save as `job-info.md` in the new job folder
3. **Populate basic information**:
   - **ID**: Use the generated job ID
   - **Job Position**: Extract from job description
   - **Company**: Extract from job description
   - **Location**: Extract from job description
   - **URL**: If provided, otherwise mark as "Not provided"
4. **Populate job details**:
   - **Description**: Paste the full job description
5. **Set initial tracking**:
   - **Status**: Set to "Saved"
   - **Date Saved**: Current date
   - **Excitement**: Set to "TBD" (to be determined by user)
   - Leave other fields empty for user to fill

### Step 3: Update Tracker CSV
1. **Read current tracker**: Load `tracker-example.csv`
2. **Add new entry**: Add a new row with:
   - **ID**: Generated job ID
   - **Job Position**: Extracted job title
   - **Company**: Extracted company name
   - **Max. Salary**: "TBD"
   - **Location**: Extracted location
   - **Status**: "Saved"
   - **Date Saved**: Current date
   - **Deadline**: "TBD"
   - **Date Applied**: Empty
   - **Follow up**: Empty
   - **Excitement**: "TBD"
3. **Save tracker**: Update the CSV file

### Step 4: Create Requirements Analysis File
1. **Copy template**: Use `@requirements-template.csv` as the base template
2. **Create file**: Save as `requirements.csv` in the new job folder
3. **Analyze job description** and extract requirements:
   - **Required skills** (programming languages, frameworks, tools)
   - **Desired qualifications** (education, experience, certifications)
   - **Soft skills** (leadership, communication, etc.)
   - **Industry knowledge** (domain expertise, regulations, etc.)
   - **Technical requirements** (systems, platforms, methodologies)

### Step 5: Analyze Meta CV and Cover Letter Examples
1. **Read meta CV example**: Analyze `@meta-cv-example.json`
2. **Read meta cover letter example**: Analyze `@meta-cover-letter-example.json`
3. **Cross-reference with job requirements**:
   - Identify which CV sections match job requirements
   - Identify which cover letter paragraphs are relevant
   - Note gaps between candidate profile and job requirements
   - Identify strengths to highlight

### Step 6: Populate Requirements Template
1. **For each job requirement**, create a row in `requirements.csv`:
   - **Criteria**: The specific requirement from job description
   - **Required/Desired**: Mark as "Required" or "Desired" based on job description language
   - **CV Evidence**: Reference specific sections/entries from meta CV that address this requirement
   - **Personal Statement Evidence**: Reference specific paragraphs from meta cover letter that address this requirement
   - **Strength Level**: Assess how well the candidate meets this requirement (Strong/Moderate/Weak/None)
   - **Score (1-10)**: Numeric score based on strength level
   - **How to Improve**: Specific actions to strengthen this area
   - **Notes**: Additional observations or context
   - **Action Items**: Concrete steps to address gaps

### Step 7: Generate Analysis Report
1. **Create analysis summary** including:
   - **Overall Match Score**: Average of all requirement scores
   - **Strong Areas**: Requirements where candidate scores 8-10
   - **Moderate Areas**: Requirements where candidate scores 5-7
   - **Weak Areas**: Requirements where candidate scores 1-4
   - **Missing Areas**: Requirements where candidate scores 0
   - **Priority Actions**: Top 3-5 action items to improve candidacy
   - **CV Customization**: Specific CV sections to emphasize
   - **Cover Letter Focus**: Key points to highlight in cover letter

2. **Save report**: Create `analysis-report.md` in the job folder

3. **Conditional reporting** (if `reporting_preferences.save_reports` is true):
   - **Generate timestamp**: Use current date/time if `include_timestamps` is true
   - **Create report filename**: `new-job-analysis-{job_id}-{timestamp}.md` (if timestamps enabled) or `new-job-analysis-{job_id}.md`
   - **Save to reports folder**: `reports/new-job-analysis-{job_id}-{timestamp}.md`
   - **Include detailed analysis** (if `detailed_analysis` is true):
     - **Technical details**: Processing steps, data sources, validation results
     - **Metadata information** (if `include_metadata` is true): File paths, processing times, system information
     - **Quality metrics**: Data completeness, accuracy scores, validation results
   - **Generate JSON report** (if `report_format` is "json" or "both"):
     - **Create JSON version**: `reports/new-job-analysis-{job_id}-{timestamp}.json`
     - **Include structured data**: All analysis results in JSON format

## File Structure After Processing
```
jobs/
└── JOB_YYYYMMDD_XXX/
    ├── job-info.md
    ├── requirements.csv
    └── analysis-report.md
```

## Quality Checks
Before completing, verify:
- [ ] Job folder created with correct naming
- [ ] Job info file populated with all available information
- [ ] Tracker CSV updated with new entry
- [ ] Requirements CSV contains all identified job requirements
- [ ] Analysis report provides actionable insights
- [ ] All files are properly formatted and readable

## Error Handling
- If job description is incomplete, note missing information in job-info.md
- If requirements are unclear, mark as "TBD" and note in analysis
- If meta CV/cover letter examples are missing, proceed with available information
- Always save partial progress and note what needs manual completion

## Output Format
The agent should provide a summary of:
1. **Job folder created**: `jobs/JOB_YYYYMMDD_XXX/`
2. **Files created**: List of all files created
3. **Key findings**: Brief summary of analysis results
4. **Next steps**: Recommended actions for the user

## Notes
- Always preserve original job description text
- Use consistent naming conventions
- Maintain CSV formatting standards
- Provide clear, actionable recommendations
- Focus on specific, measurable improvements
