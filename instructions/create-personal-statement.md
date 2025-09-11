# Create Personal Statement Instructions

## Overview
This document provides step-by-step instructions for generating a targeted personal statement based on job requirements analysis. The agent should use the requirements table from a specific job folder to create a customized personal statement.

## Prerequisites
- **MANDATORY**: Read and load user rules file (`@rules/user-rules.json` or `@rules/rules-default.json`) before starting
- Job folder with `requirements.csv` file
- Access to `@personal-statement-template.md` template
- Access to meta cover letter JSON files (meta-cover-letter-template.json, meta-cover-letter-example.json)
- Write permissions to create files in the job folder

## Step-by-Step Process

### Step 1: Locate and Analyze Requirements
1. **Navigate to job folder**: Use the provided job folder path
2. **Read requirements.csv**: Load the requirements analysis file
3. **Extract Personal Statement Evidence IDs**: Collect all IDs from the "Personal Statement Evidence" column
4. **Identify priority requirements**: Focus on "Required" criteria first, then "Desired"
5. **Note scoring patterns**: Pay attention to high-scoring requirements (8-10) to emphasize
6. **Analyze job context**: Understand the role, company, and industry context

### Step 2: Load Meta Cover Letter Data
1. **Read meta cover letter template**: Load `@meta-cover-letter-template.json` for structure reference
2. **Read meta cover letter example**: Load `@meta-cover-letter-example.json` for content examples
3. **Create content mapping**: Map Personal Statement Evidence IDs to actual paragraph content from meta cover letter files

### Step 3: Determine Personal Statement Length and Focus
1. **Check prompt for length specification**: Look for length requirements in the user prompt
2. **Default length**: If not specified, use "medium" length as default
3. **Focus areas**: Prioritize content based on job requirements:
   - High-scoring requirements (8-10): Emphasize heavily
   - Moderate requirements (5-7): Include with context
   - Low-scoring requirements (1-4): Minimize or omit
   - Missing requirements (0): Omit unless critical

### Step 4: Select and Customize Paragraphs
1. **Choose paragraph types**: Select from available types based on job requirements:
   - **Introduction**: Express interest and connection to role
   - **Experience**: Highlight relevant professional background
   - **Skills**: Demonstrate technical and soft skills
   - **Achievement**: Showcase specific accomplishments
   - **Company Research**: Display knowledge of target company
   - **Value Proposition**: Explain why you're the right fit
   - **Technical**: Deep dive into technical expertise
   - **Leadership**: Highlight management and team leadership
   - **Passion**: Show personal motivation and interests
   - **Problem Solving**: Demonstrate analytical approach
   - **Collaboration**: Show teamwork and communication skills

2. **Customize paragraph content**:
   - Replace placeholder fields with job-specific information
   - Incorporate keywords from job description
   - Ensure tone matches job and company culture
   - Maintain professional yet engaging voice

### Step 5: Choose Structure Approach and Build Personal Statement
1. **Analyze job nature** to determine optimal structure approach:
   - **Technical roles**: Focus on problem-solving, technical expertise, quantifiable results
   - **Creative roles**: Emphasize innovation, passion, creative projects, collaboration
   - **Leadership roles**: Highlight management experience, strategic thinking, team building
   - **Entry-level roles**: Emphasize education, potential, enthusiasm, relevant projects

2. **Select structure approach** based on job nature and requirements:

#### **Default Skeleton (Safe Choice)**
- **Introduction**: Express interest and connection to role
- **Experience**: Highlight relevant professional background
- **Skills**: Demonstrate required technical and soft skills
- **Achievement**: Showcase quantifiable accomplishments
- **Company Research**: Display knowledge of target company
- **Closing**: Reinforce interest and value proposition

#### **Story-First Approach** (Best for: Creative, Marketing, Sales, Customer-facing roles)
- **Opening Story**: Start with a compelling personal/professional anecdote
- **Experience**: Connect story to relevant work experience
- **Skills**: Demonstrate capabilities through narrative
- **Achievement**: Showcase results that validate the story
- **Company Alignment**: Connect personal journey to company mission
- **Closing**: Reinforce the narrative arc

#### **Achievement-First Approach** (Best for: Technical, Data, Engineering, Results-driven roles)
- **Opening Impact**: Start with a quantified impact statement
- **Experience**: Provide context for the achievement
- **Skills**: Detail the technical capabilities used
- **Additional Achievements**: Showcase other relevant accomplishments
- **Company Value**: Explain how achievements translate to company needs
- **Closing**: Emphasize continued impact potential

#### **Company-First Approach** (Best for: Mission-driven, Non-profit, Startup, Culture-focused roles)
- **Company Mission**: Open with alignment to company mission/values
- **Personal Connection**: Explain why this mission resonates personally
- **Experience**: Show relevant experience that supports the mission
- **Skills**: Demonstrate capabilities that advance the mission
- **Achievement**: Showcase results that align with company goals
- **Closing**: Reinforce commitment to company vision

3. **Build the personal statement** using the selected approach:
   - **Create compelling opening** based on chosen approach
   - **Develop body paragraphs** following the selected structure
   - **Ensure smooth transitions** between paragraphs
   - **Maintain consistent tone** throughout
   - **Create strong closing** that reinforces the chosen approach

### Step 6: Customize for Job Requirements
1. **Emphasize matching qualifications**: Highlight skills that directly match job requirements
2. **Use job-specific language**: Incorporate terminology and phrases from job description
3. **Show cultural fit**: Demonstrate alignment with company values and mission
4. **Address specific needs**: Reference specific challenges or projects mentioned in job description
5. **Quantify impact**: Include metrics and results where possible

### Step 7: Ensure Coherence and Flow
1. **Check paragraph transitions**: Ensure smooth flow between paragraphs
2. **Maintain consistent tone**: Keep professional yet engaging throughout
3. **Verify logical progression**: Ensure the statement builds a compelling narrative
4. **Check for repetition**: Avoid repeating the same points
5. **Ensure completeness**: Cover all high-priority requirements

### Step 8: Format and Finalize
1. **Follow template structure**: Maintain the markdown format from personal-statement-template.md
2. **Ensure consistency**: Use consistent formatting and terminology
3. **Check length**: Verify the statement fits within specified length requirements
4. **Proofread**: Check for typos, grammar, and formatting issues
5. **Validate content**: Ensure all Personal Statement Evidence IDs have been properly incorporated

### Step 9: Save and Document
1. **Save personal statement file**: Create `personal-statement.md` in the job folder
2. **Create generation log**: Document which Personal Statement Evidence IDs were used
3. **Note customizations**: Record any job-specific modifications made

4. **Conditional reporting** (if `reporting_preferences.save_reports` is true):
   - **Generate timestamp**: Use current date/time if `include_timestamps` is true
   - **Create report filename**: `personal-statement-generation-{job_id}-{timestamp}.md` (if timestamps enabled) or `personal-statement-generation-{job_id}.md`
   - **Save to reports folder**: `reports/personal-statement-generation-{job_id}-{timestamp}.md`
   - **Include detailed analysis** (if `detailed_analysis` is true):
     - **Structure selection rationale**: Why specific structure approach was chosen
     - **Content selection rationale**: Why specific paragraphs were chosen
     - **Template customization**: How templates were adapted for the job
     - **Writing style application**: How user's voice was preserved
     - **Quality metrics**: Content relevance scores, completeness assessment
   - **Include metadata** (if `include_metadata` is true):
     - **Source files**: Which meta cover letter entries were used
     - **Processing steps**: Step-by-step generation process
     - **Customization details**: Specific adaptations made
     - **Structure approach**: Which structure was selected and why
   - **Generate JSON report** (if `report_format` is "json" or "both"):
     - **Create JSON version**: `reports/personal-statement-generation-{job_id}-{timestamp}.json`
     - **Include structured data**: All generation details in JSON format

## Content Selection Criteria

### High Priority (Must Include)
- Requirements with score 8-10
- Skills directly mentioned in job description
- Recent and relevant experience
- Quantified achievements
- Required qualifications
- Company-specific knowledge

### Medium Priority (Include if Space Allows)
- Requirements with score 5-7
- Transferable skills
- Relevant projects
- Soft skills mentioned in job
- Industry knowledge

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

### Short Personal Statement (1-2 paragraphs)
- Focus on most relevant experience and skills
- Include key achievement with metrics
- Express genuine interest and value proposition
- Keep concise and impactful

### Medium Personal Statement (3-4 paragraphs) - Default
- Include relevant experience and skills
- Showcase 1-2 key achievements
- Display company knowledge
- Explain value proposition
- Maintain engaging tone

### Long Personal Statement (5+ paragraphs)
- Comprehensive coverage of relevant experience
- Multiple achievements with context
- Detailed company research
- Strong value proposition
- Personal motivation and passion
- Future goals and aspirations

## Structure Selection Guide

### **Default Skeleton** (Safe Choice)
- **Best for**: Traditional corporate roles, consulting, finance, general business
- **Emphasize**: Experience, Skills, Achievement, Company Research
- **Tone**: Professional, balanced, comprehensive
- **Use when**: Job requirements are broad or unclear, or when multiple approaches could work

### **Story-First Approach**
- **Best for**: Creative, Marketing, Sales, Customer-facing, Brand-focused roles
- **Emphasize**: Passion, Experience (narrative), Achievement (story-driven), Company Alignment
- **Tone**: Engaging, personal, compelling, authentic
- **Use when**: Company values creativity, personal connection matters, role requires storytelling

### **Achievement-First Approach**
- **Best for**: Technical, Data, Engineering, Results-driven, Performance-focused roles
- **Emphasize**: Achievement, Technical, Problem Solving, Experience (context)
- **Tone**: Confident, analytical, results-oriented, professional
- **Use when**: Quantifiable results are key, technical expertise is primary, performance matters most

### **Company-First Approach**
- **Best for**: Mission-driven, Non-profit, Startup, Culture-focused, Values-based roles
- **Emphasize**: Company Research, Passion, Experience (mission-aligned), Value Proposition
- **Tone**: Enthusiastic, mission-driven, authentic, committed
- **Use when**: Company mission is prominent, cultural fit is crucial, values alignment matters

## Paragraph Selection Strategy by Role Type

### For Technical Roles
- **Structure**: Achievement-First or Default Skeleton
- **Emphasize**: Technical, Experience, Achievement, Problem Solving
- **Include**: Specific technologies, methodologies, quantifiable results
- **Tone**: Professional, analytical, confident

### For Leadership Roles
- **Structure**: Default Skeleton or Story-First
- **Emphasize**: Leadership, Experience, Achievement, Value Proposition
- **Include**: Team management, strategic thinking, results, vision
- **Tone**: Authoritative, confident, inspiring

### For Creative Roles
- **Structure**: Story-First or Company-First
- **Emphasize**: Passion, Experience (narrative), Achievement (creative), Collaboration
- **Include**: Creative projects, innovation, teamwork, portfolio pieces
- **Tone**: Enthusiastic, creative, engaging, authentic

### For Entry-Level Roles
- **Structure**: Company-First or Default Skeleton
- **Emphasize**: Education, Skills, Passion, Value Proposition
- **Include**: Relevant coursework, projects, internships, potential
- **Tone**: Enthusiastic, eager, professional, growth-oriented

## Quality Checks
Before completing, verify:
- [ ] All high-priority requirements addressed
- [ ] Personal Statement Evidence IDs properly incorporated
- [ ] Job-specific keywords included
- [ ] Company knowledge displayed
- [ ] Quantified achievements highlighted
- [ ] Length requirements met
- [ ] Formatting consistent
- [ ] No typos or errors
- [ ] Coherent narrative flow
- [ ] Professional yet engaging tone

## Error Handling
- If Personal Statement Evidence ID not found, note in generation log
- If content doesn't fit length requirements, prioritize by relevance score
- If meta cover letter data is incomplete, use available information and note gaps
- Always save partial progress and note what needs manual completion

## Output Format
The agent should provide:
1. **Personal statement file created**: `jobs/[JOB_ID]/personal-statement.md`
2. **Content summary**: Brief overview of what was included
3. **Customization notes**: Key modifications made for this job
4. **Missing elements**: Any Personal Statement Evidence IDs that couldn't be found
5. **Length achieved**: Final word count or paragraph count

## Notes
- Always preserve the original template structure
- Use consistent formatting and terminology
- Focus on relevance to job requirements
- Maintain professional yet engaging tone throughout
- Ensure all content is accurate and current
- Show genuine interest and enthusiasm for the specific role
