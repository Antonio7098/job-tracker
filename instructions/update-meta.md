# Update Meta Documents Instructions

## Overview
This document provides step-by-step instructions for updating meta CV and cover letter documents with new data. The agent should follow these instructions when given new information (user-provided text, linked CV, or personal statement) to add or update entries in the meta databases.

## Prerequisites
- **MANDATORY**: Read and load user rules file (`@rules/user-rules.json` or `@rules/rules-default.json`) before starting
- New data provided by user (text, CV, personal statement, or other content)
- Access to existing meta CV and cover letter files
- Write permissions to update meta files
- Understanding of the meta document schemas

## Step-by-Step Process

### Step 1: Analyze Input Data
1. **Identify data type**:
   - **CV/Resume**: Structured professional information
   - **Personal Statement/Cover Letter**: Written content for applications
   - **Raw Text**: Unstructured information to be categorized
   - **Linked Document**: URL or file reference to process

2. **Extract key information**:
   - **Personal Information**: Name, contact details, location
   - **Professional Experience**: Jobs, roles, achievements, dates
   - **Education**: Degrees, institutions, dates, achievements
   - **Skills**: Technical, soft skills, proficiency levels
   - **Projects**: Descriptions, technologies, achievements
   - **Content**: Paragraphs, sections, themes, tone

3. **Determine update scope**:
   - **New entries only**: Add new information without modifying existing
   - **Update existing**: Modify existing entries with new information
   - **Mixed approach**: Both new and updated entries

### Step 2: Process Meta CV Updates
1. **Read current meta CV**: Load `@meta/my-meta-cv.json` (or `@meta/meta-cv-example.json` if user file doesn't exist)

2. **For each new/updated CV entry**:
   - **Generate unique ID**: Use format `{category}_{XXX}` (e.g., `work_003`, `proj_004`)
   - **Extract structured data**: Follow the meta CV schema
   - **Add rich metadata**: Include display_priority, searchable, keywords, etc.
   - **Preserve user's writing style**: Follow rules for writing style preservation

3. **Update specific sections**:
   - **Personal Info**: Update contact details, location, etc.
   - **Education**: Add new degrees, certifications, courses
   - **Work Experience**: Add new jobs, update existing roles
   - **Projects**: Add new projects, update existing ones
   - **Technical Skills**: Add new skills, update proficiency levels
   - **Soft Skills**: Add new soft skills, update existing ones
   - **Certifications**: Add new certifications, update existing ones
   - **Publications**: Add new publications, update existing ones
   - **Languages**: Add new languages, update proficiency
   - **Interests**: Add new interests, update existing ones

4. **Ensure data consistency**:
   - **Check for duplicates**: Avoid duplicate entries
   - **Validate dates**: Ensure chronological consistency
   - **Verify references**: Check that all references are valid
   - **Maintain schema compliance**: Follow the established JSON schema

### Step 3: Process Meta Cover Letter Updates
1. **Read current meta cover letter**: Load `@meta/my-meta-cover-letter.json` (or `@meta/meta-cover-letter-example.json` if user file doesn't exist)

2. **For each new/updated paragraph**:
   - **Generate unique ID**: Use format `{type}_{XXX}` (e.g., `intro_003`, `experience_004`)
   - **Categorize paragraph type**: Introduction, experience, skills, achievement, etc.
   - **Extract content**: Clean and format the paragraph text
   - **Add rich metadata**: Include all required metadata fields
   - **Preserve user's writing style**: Follow rules for writing style preservation

3. **Update specific paragraph types**:
   - **Introduction**: New opening paragraphs for different contexts
   - **Experience**: New experience descriptions and stories
   - **Skills**: New skill descriptions and examples
   - **Achievement**: New achievement stories and quantifiable results
   - **Company Research**: New company-specific content
   - **Value Proposition**: New value proposition statements
   - **Closing**: New closing paragraphs
   - **Technical**: New technical content
   - **Leadership**: New leadership examples
   - **Passion**: New passion and motivation content

4. **Ensure content quality**:
   - **Check for duplicates**: Avoid duplicate paragraphs
   - **Validate tone consistency**: Ensure tone matches user preferences
   - **Verify customization fields**: Include proper customizable fields
   - **Maintain schema compliance**: Follow the established JSON schema

### Step 4: Apply Writing Style Preservation Rules
1. **Read user rules**: Load writing style preservation settings from rules file

2. **For each new entry**:
   - **Preserve authentic voice**: Maintain user's natural writing style
   - **Apply adaptation approach**: Use smooth_integration or other specified approach
   - **Maintain voice consistency**: Ensure consistent tone throughout
   - **Preserve sentence structure**: Keep user's natural sentence patterns
   - **Adapt vocabulary appropriately**: Use user's preferred terms and phrases
   - **Handle tone transitions**: Apply gradual_transition or other specified approach

3. **Quality checks**:
   - **Readability**: Ensure content is clear and professional
   - **Consistency**: Check for consistent voice and tone
   - **Authenticity**: Verify content sounds like the user wrote it
   - **Relevance**: Ensure content is relevant and useful

### Step 5: Update Meta Files
1. **Backup existing files**: Create backup copies before updating
2. **Update meta CV**: Save updated `@meta/my-meta-cv.json`
3. **Update meta cover letter**: Save updated `@meta/my-meta-cover-letter.json`
4. **Validate JSON**: Ensure both files are valid JSON
5. **Verify schema compliance**: Check that both files follow their schemas

### Step 6: Generate Update Report
1. **Create summary report** including:
   - **New CV entries**: List of all new CV entries added
   - **Updated CV entries**: List of all CV entries modified
   - **New cover letter paragraphs**: List of all new paragraphs added
   - **Updated cover letter paragraphs**: List of all paragraphs modified
   - **Data quality metrics**: Number of entries, completeness scores
   - **Writing style compliance**: How well the updates preserve user's voice

2. **Save report**: Create `meta-update-report.md` in the root directory

3. **Conditional reporting** (if `reporting_preferences.save_reports` is true):
   - **Generate timestamp**: Use current date/time if `include_timestamps` is true
   - **Create report filename**: `meta-update-{timestamp}.md` (if timestamps enabled) or `meta-update.md`
   - **Save to reports folder**: `reports/meta-update-{timestamp}.md`
   - **Include detailed analysis** (if `detailed_analysis` is true):
     - **Processing steps**: Step-by-step update process
     - **Data validation results**: Schema compliance, data quality checks
     - **Writing style analysis**: How well user's voice was preserved
     - **Quality metrics**: Completeness scores, accuracy assessments
   - **Include metadata** (if `include_metadata` is true):
     - **Source files**: Which input files were processed
     - **Processing times**: Time taken for each step
     - **System information**: Version details, processing environment
     - **Validation results**: Detailed validation outcomes
   - **Generate JSON report** (if `report_format` is "json" or "both"):
     - **Create JSON version**: `reports/meta-update-{timestamp}.json`
     - **Include structured data**: All update details in JSON format

## File Structure After Processing
```
meta/
├── my-meta-cv.json (updated)
├── my-meta-cover-letter.json (updated)
└── meta-cv-example.json (unchanged)
└── meta-cover-letter-example.json (unchanged)

meta-update-report.md (new)
```

## Quality Checks
Before completing, verify:
- [ ] All new entries have unique IDs
- [ ] All entries follow the correct schema
- [ ] Writing style preservation rules are applied
- [ ] No duplicate entries were created
- [ ] All dates are chronologically consistent
- [ ] All metadata is complete and accurate
- [ ] JSON files are valid and properly formatted
- [ ] User's authentic voice is preserved

## Error Handling
- If input data is incomplete, note missing information in the report
- If schema validation fails, fix the issues before saving
- If writing style preservation fails, note the issues and provide alternatives
- Always save partial progress and note what needs manual completion
- If user rules conflict with data, prioritize user rules

## Output Format
The agent should provide a summary of:
1. **New CV entries added**: Count and brief descriptions
2. **Updated CV entries**: Count and brief descriptions
3. **New cover letter paragraphs added**: Count and brief descriptions
4. **Updated cover letter paragraphs**: Count and brief descriptions
5. **Data quality assessment**: Overall quality of the updates
6. **Writing style compliance**: How well the updates preserve user's voice
7. **Next steps**: Recommendations for further improvements

## Notes
- Always preserve the user's authentic writing style
- Use consistent ID generation patterns
- Maintain high data quality standards
- Follow the established schemas exactly
- Provide clear, actionable feedback
- Focus on content that will be useful for future applications
