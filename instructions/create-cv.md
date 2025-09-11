# Create CV Instructions

## Overview
This document provides step-by-step instructions for generating a targeted CV based on job requirements analysis. The agent should use the requirements table from a specific job folder to create a customized CV.

## Prerequisites
- **MANDATORY**: Read and load user rules file (`@rules/user-rules.json` or `@rules/rules-default.json`) before starting
- Job folder with `requirements.csv` file
- Access to `@cv-template.md` template
- Access to meta CV JSON files (meta-cv-template.json, meta-cv-example.json)
- Write permissions to create files in the job folder

## Step-by-Step Process

### Step 1: Locate and Analyze Requirements
1. **Navigate to job folder**: Use the provided job folder path
2. **Read requirements.csv**: Load the requirements analysis file
3. **Extract CV Evidence IDs**: Collect all IDs from the "CV Evidence" column
4. **Identify priority requirements**: Focus on "Required" criteria first, then "Desired"
5. **Note scoring patterns**: Pay attention to high-scoring requirements (8-10) to emphasize

### Step 2: Load Meta CV Data
1. **Read meta CV template**: Load `@meta-cv-template.json` for structure reference
2. **Read meta CV example**: Load `@meta-cv-example.json` for content examples
3. **Create content mapping**: Map CV Evidence IDs to actual content from meta CV files

### Step 3: Determine CV Length and Focus
1. **Check prompt for length specification**: Look for length requirements in the user prompt
2. **Default length**: If not specified, use "2_pages" as default
3. **Focus areas**: Prioritize sections based on job requirements:
   - High-scoring requirements (8-10): Emphasize heavily
   - Moderate requirements (5-7): Include with context
   - Low-scoring requirements (1-4): Minimize or omit
   - Missing requirements (0): Omit unless critical

### Step 4: Generate CV Content
1. **Start with template**: Use `@cv-template.md` as the base structure
2. **Populate Personal Information**:
   - Use data from meta CV personal_information section
   - Ensure all contact details are current
   - Include relevant online presence links

3. **Create Profile Section**:
   - Use profile summary from meta CV
   - Customize to highlight job-relevant skills
   - Keep within 2-3 sentences as per template

4. **Populate Education**:
   - Include all relevant education entries
   - Prioritize by relevance_score and display_priority
   - Include achievements and relevant coursework

5. **Add Professional Development**:
   - Include certifications and courses
   - Prioritize by relevance to job requirements
   - Include credential URLs if available

6. **Build Work Experience**:
   - Select most relevant work experiences
   - Prioritize by relevance_score and job alignment
   - Include quantified achievements
   - Emphasize technologies and skills mentioned in job requirements

7. **Add Technical Projects**:
   - Include projects that demonstrate required skills
   - Prioritize by complexity and relevance
   - Include URLs and key results

8. **Populate Technical Skills**:
   - Organize by categories (programming languages, frameworks, etc.)
   - Prioritize skills mentioned in job requirements
   - Include proficiency levels and years of experience
   - Group related skills logically

9. **Add Additional Sections**:
   - Include soft skills relevant to the role
   - Add languages if relevant to job requirements
   - Include achievements and awards
   - Add publications if relevant
   - Include volunteer experience if relevant

### Step 5: Customize for Job Requirements
1. **Emphasize matching skills**: Highlight skills that directly match job requirements
2. **Use job-specific keywords**: Incorporate terminology from job description
3. **Quantify achievements**: Include metrics and results where possible
4. **Show progression**: Demonstrate career growth and increasing responsibility
5. **Address gaps**: If possible, show transferable skills for missing requirements

### Step 6: Format and Finalize
1. **Follow template structure**: Maintain the markdown format from cv-template.md
2. **Ensure consistency**: Use consistent formatting throughout
3. **Check length**: Verify the CV fits within specified length requirements
4. **Proofread**: Check for typos and formatting issues
5. **Validate content**: Ensure all CV Evidence IDs have been properly incorporated

### Step 7: Save and Document
1. **Save CV file**: Create `cv.md` in the job folder
2. **Create generation log**: Document which CV Evidence IDs were used
3. **Note customizations**: Record any job-specific modifications made

4. **Conditional reporting** (if `reporting_preferences.save_reports` is true):
   - **Generate timestamp**: Use current date/time if `include_timestamps` is true
   - **Create report filename**: `cv-generation-{job_id}-{timestamp}.md` (if timestamps enabled) or `cv-generation-{job_id}.md`
   - **Save to reports folder**: `reports/cv-generation-{job_id}-{timestamp}.md`
   - **Include detailed analysis** (if `detailed_analysis` is true):
     - **Content selection rationale**: Why specific CV entries were chosen
     - **Template customization**: How templates were adapted for the job
     - **Writing style application**: How user's voice was preserved
     - **Quality metrics**: Content relevance scores, completeness assessment
   - **Include metadata** (if `include_metadata` is true):
     - **Source files**: Which meta CV entries were used
     - **Processing steps**: Step-by-step generation process
     - **Customization details**: Specific adaptations made
   - **Generate JSON report** (if `report_format` is "json" or "both"):
     - **Create JSON version**: `reports/cv-generation-{job_id}-{timestamp}.json`
     - **Include structured data**: All generation details in JSON format

## Content Selection Criteria

### High Priority (Must Include)
- Requirements with score 8-10
- Skills directly mentioned in job description
- Recent and relevant experience
- Quantified achievements
- Required qualifications

### Medium Priority (Include if Space Allows)
- Requirements with score 5-7
- Transferable skills
- Relevant projects
- Additional certifications
- Soft skills mentioned in job

### Low Priority (Include Only if Critical)
- Requirements with score 1-4
- Older or less relevant experience
- Generic skills
- Personal interests (unless specifically relevant)

### Exclude
- Requirements with score 0
- Completely irrelevant experience
- Outdated technologies
- Personal information not relevant to job

## Length Guidelines

### 1 Page CV
- Focus on most relevant 2-3 work experiences
- Include only top 5-7 technical skills
- Minimal project details
- Essential education only

### 2 Page CV (Default)
- Include 3-4 most relevant work experiences
- Comprehensive technical skills section
- 2-3 key projects with details
- Full education and certifications

### 3+ Page CV
- Include all relevant work experience
- Detailed technical skills with proficiency levels
- Multiple projects with full descriptions
- All education, certifications, and achievements

## Quality Checks
Before completing, verify:
- [ ] All high-priority requirements addressed
- [ ] CV Evidence IDs properly incorporated
- [ ] Job-specific keywords included
- [ ] Quantified achievements highlighted
- [ ] Length requirements met
- [ ] Formatting consistent
- [ ] No typos or errors
- [ ] Contact information current

## Error Handling
- If CV Evidence ID not found, note in generation log
- If content doesn't fit length requirements, prioritize by relevance score
- If meta CV data is incomplete, use available information and note gaps
- Always save partial progress and note what needs manual completion

## Output Format
The agent should provide:
1. **CV file created**: `jobs/[JOB_ID]/cv.md`
2. **Content summary**: Brief overview of what was included
3. **Customization notes**: Key modifications made for this job
4. **Missing elements**: Any CV Evidence IDs that couldn't be found
5. **Length achieved**: Final page count or word count

## Notes
- Always preserve the original template structure
- Use consistent formatting and terminology
- Focus on relevance to job requirements
- Maintain professional tone throughout
- Ensure all content is accurate and current
