# Troubleshooting Guide

## Common Issues and Solutions

### Configuration Issues

#### JSON Validation Errors
**Problem**: Invalid JSON format in configuration files
**Symptoms**: 
- Error messages about JSON syntax
- System fails to load configuration
- Missing or incorrect data

**Solutions**:
1. **Validate JSON syntax**:
   ```bash
   # Use online JSON validator or command line tool
   python -m json.tool rules/user-rules.json
   ```

2. **Check common issues**:
   - Missing commas between objects
   - Unclosed brackets or braces
   - Incorrect quotes (use double quotes)
   - Trailing commas in arrays

3. **Use a JSON editor**:
   - VS Code with JSON extension
   - Online JSON editors
   - JSON linting tools

**Prevention**:
- Always validate JSON before saving
- Use a proper JSON editor
- Test configuration changes incrementally

#### Missing Required Fields
**Problem**: Required fields missing from configuration
**Symptoms**:
- System errors about missing fields
- Default values not applied
- Unexpected behavior

**Solutions**:
1. **Check against template**:
   - Compare with `templates/rules-template.json`
   - Ensure all required fields are present
   - Use `rules-default.json` as reference

2. **Validate field types**:
   - Ensure correct data types (string, number, boolean)
   - Check enum values are valid
   - Verify required fields are not null

3. **Use default values**:
   - Copy from `rules-default.json`
   - Start with minimal configuration
   - Add complexity gradually

**Prevention**:
- Always start with default configuration
- Validate against schema
- Test changes incrementally

### Content Generation Issues

#### No Content Generated
**Problem**: System generates empty or minimal content
**Symptoms**:
- Empty CV or personal statement
- Missing sections
- Generic placeholder content

**Solutions**:
1. **Check quality thresholds**:
   ```json
   "quality_thresholds": {
     "minimum_relevance_score": 0.3,  // Lower from 0.6
     "minimum_requirement_score": 0.3  // Lower from 0.5
   }
   ```

2. **Verify meta content**:
   - Ensure meta CV/cover letter files exist
   - Check content has proper metadata
   - Verify relevance scores are set

3. **Review job requirements**:
   - Check if requirements are too specific
   - Ensure job description was parsed correctly
   - Look for missing keywords

4. **Check content selection**:
   - Review requirements analysis
   - Verify CV/Personal Statement Evidence IDs
   - Check if content matches job requirements

**Prevention**:
- Maintain comprehensive meta content
- Set appropriate quality thresholds
- Regularly update content libraries

#### Wrong Content Selected
**Problem**: Irrelevant or inappropriate content selected
**Symptoms**:
- Content doesn't match job requirements
- Wrong tone or style
- Inappropriate sections included

**Solutions**:
1. **Adjust quality thresholds**:
   - Increase minimum relevance score
   - Set higher requirement scores
   - Fine-tune selection criteria

2. **Update meta content metadata**:
   - Improve relevance scores
   - Add better keywords
   - Set appropriate target audiences

3. **Refine job requirements analysis**:
   - Check requirements extraction
   - Verify keyword matching
   - Review industry/role alignment

4. **Customize content selection**:
   - Use always/never include sections
   - Add custom phrases
   - Set avoid words

**Prevention**:
- Regularly review and update meta content
- Test with different job types
- Monitor content selection patterns

#### Formatting Issues
**Problem**: Generated content has formatting problems
**Symptoms**:
- Incorrect markdown formatting
- Missing sections or headers
- Inconsistent styling

**Solutions**:
1. **Check template structure**:
   - Verify template files are correct
   - Ensure proper markdown formatting
   - Check section headers

2. **Review formatting preferences**:
   ```json
   "formatting_preferences": {
     "date_format": "MM/YYYY",
     "bullet_style": "dash",
     "section_headers": "title_case"
   }
   ```

3. **Validate markdown output**:
   - Use markdown validator
   - Check for proper formatting
   - Ensure consistent styling

4. **Test with different templates**:
   - Try different CV templates
   - Test personal statement structures
   - Verify formatting consistency

**Prevention**:
- Use validated templates
- Test formatting with sample content
- Regular template maintenance

### File System Issues

#### Missing Files
**Problem**: Required files not found
**Symptoms**:
- File not found errors
- Missing content or templates
- System fails to process jobs

**Solutions**:
1. **Check file paths**:
   - Verify files exist in correct locations
   - Check file permissions
   - Ensure proper directory structure

2. **Create missing files**:
   - Copy from templates
   - Use example files as reference
   - Generate from scratch if needed

3. **Verify file permissions**:
   - Check read/write permissions
   - Ensure proper access rights
   - Fix permission issues

**Prevention**:
- Maintain proper file structure
- Regular file system checks
- Backup important files

### Meta Content Update Issues

#### Update Failures
**Problem**: Meta content updates not working
**Symptoms**:
- No new entries added
- Update process fails
- Schema validation errors

**Solutions**:
1. **Check input data format**:
   - Ensure CV/resume is properly formatted
   - Verify personal statement is complete
   - Check raw text has sufficient context

2. **Validate JSON schemas**:
   ```bash
   python -m json.tool meta/my-meta-cv.json
   python -m json.tool meta/my-meta-cover-letter.json
   ```

3. **Check file permissions**:
   - Ensure write access to meta files
   - Verify backup creation works
   - Check reports folder permissions

4. **Review update instructions**:
   - Follow `@instructions/update-meta.md` exactly
   - Check user rules for conflicts
   - Verify data categorization

**Prevention**:
- Regular schema validation
- Test updates with sample data
- Maintain file permissions

#### Writing Style Preservation Issues
**Problem**: Updated content doesn't match user's voice
**Symptoms**:
- Content sounds generic
- Inconsistent tone
- Lost personal expressions

**Solutions**:
1. **Check writing style rules**:
   - Verify `writing_style_preservation` settings
   - Ensure `preserve_authentic_voice` is true
   - Check adaptation approach settings

2. **Review source content**:
   - Ensure input data reflects user's voice
   - Check for sufficient personal content
   - Verify context is provided

3. **Adjust preservation settings**:
   - Increase voice consistency settings
   - Enable personal expression preservation
   - Set appropriate adaptation approach

**Prevention**:
- Regular style consistency checks
- Test with diverse content types
- Monitor preservation quality scores

### Reporting System Issues

#### Reports Not Generated
**Problem**: No reports created despite enabling
**Symptoms**:
- No files in reports/ folder
- Missing report references
- System completes without reports

**Solutions**:
1. **Check reporting preferences**:
   ```json
   "reporting_preferences": {
     "save_reports": true,
     "report_format": "markdown",
     "include_timestamps": true
   }
   ```

2. **Verify reports folder**:
   - Ensure reports/ folder exists
   - Check write permissions
   - Create folder if missing: `mkdir reports`

3. **Check user rules**:
   - Ensure reporting preferences are enabled
   - Verify no conflicting settings
   - Test with default rules

**Prevention**:
- Regular reporting system tests
- Monitor reports folder
- Validate user rules

#### Report Quality Issues
**Problem**: Reports missing information or low quality
**Symptoms**:
- Incomplete reports
- Missing technical details
- Poor formatting

**Solutions**:
1. **Enable detailed analysis**:
   ```json
   "detailed_analysis": true,
   "include_metadata": true
   ```

2. **Check report format**:
   - Verify markdown formatting
   - Test JSON generation if enabled
   - Review report structure

3. **Validate content sources**:
   - Ensure meta content is complete
   - Check job analysis quality
   - Verify processing steps

**Prevention**:
- Regular report quality checks
- Monitor report completeness
- Test with various job types

#### Permission Errors
**Problem**: Cannot read or write files
**Symptoms**:
- Permission denied errors
- Cannot save changes
- Files not accessible

**Solutions**:
1. **Check file permissions**:
   ```bash
   ls -la rules/user-rules.json
   chmod 644 rules/user-rules.json
   ```

2. **Fix ownership issues**:
   ```bash
   chown user:group rules/user-rules.json
   ```

3. **Check directory permissions**:
   ```bash
   chmod 755 jobs/
   chmod 755 rules/
   ```

**Prevention**:
- Set proper permissions during setup
- Regular permission audits
- Use consistent file ownership

### Performance Issues

#### Slow Processing
**Problem**: System takes too long to process jobs
**Symptoms**:
- Long wait times
- System appears frozen
- Timeout errors

**Solutions**:
1. **Check file sizes**:
   - Large meta content files slow processing
   - Consider splitting large files
   - Archive old job folders

2. **Optimize content selection**:
   - Reduce quality thresholds
   - Limit content selection criteria
   - Use more specific filters

3. **Check system resources**:
   - Monitor memory usage
   - Check disk space
   - Verify CPU usage

**Prevention**:
- Regular system maintenance
- Monitor file sizes
- Optimize content libraries

#### Memory Issues
**Problem**: System runs out of memory
**Symptoms**:
- Out of memory errors
- System crashes
- Slow performance

**Solutions**:
1. **Reduce content library size**:
   - Split large meta files
   - Remove unused content
   - Archive old data

2. **Optimize processing**:
   - Process jobs one at a time
   - Clear temporary data
   - Use streaming processing

3. **Increase system memory**:
   - Add more RAM
   - Use swap space
   - Optimize system settings

**Prevention**:
- Monitor memory usage
- Regular cleanup
- Optimize content libraries

### Content Quality Issues

#### Poor Content Quality
**Problem**: Generated content is low quality
**Symptoms**:
- Generic or template-like content
- Poor writing quality
- Inconsistent tone

**Solutions**:
1. **Improve meta content**:
   - Add more specific content
   - Improve writing quality
   - Add better examples

2. **Adjust writing style preservation**:
   ```json
   "writing_style_preservation": {
     "preserve_authentic_voice": true,
     "adaptation_approach": "smooth_integration",
     "voice_consistency": "maintain_throughout"
   }
   ```

3. **Customize content selection**:
   - Use always include sections
   - Add custom phrases
   - Set avoid words

4. **Review and edit generated content**:
   - Always review before submitting
   - Make manual improvements
   - Learn from feedback

**Prevention**:
- Maintain high-quality meta content
- Regular content review
- Continuous improvement

#### Inconsistent Voice
**Problem**: Generated content doesn't match user's voice
**Symptoms**:
- Content sounds generic
- Inconsistent tone
- Doesn't sound like user

**Solutions**:
1. **Improve writing style preservation**:
   - Set preserve_authentic_voice to true
   - Use smooth_integration approach
   - Maintain voice consistency

2. **Add custom phrases**:
   ```json
   "custom_phrases": [
     {
       "phrase": "passionate about",
       "alternative": "committed to"
     }
   ]
   ```

3. **Set avoid words**:
   ```json
   "avoid_words": [
     {
       "word": "passionate",
       "reason": "Overused in industry"
     }
   ]
   ```

4. **Improve meta content**:
   - Write content in your own voice
   - Use your natural expressions
   - Add personal touches

**Prevention**:
- Write meta content in your voice
- Regular voice consistency checks
- Continuous style refinement

## Debugging Steps

### Step 1: Check System Status
1. **Verify file structure**:
   ```bash
   ls -la
   ls -la rules/
   ls -la meta/
   ls -la templates/
   ```

2. **Check file permissions**:
   ```bash
   ls -la rules/user-rules.json
   ls -la meta/meta-cv-example.json
   ```

3. **Validate JSON files**:
   ```bash
   python -m json.tool rules/user-rules.json
   python -m json.tool meta/meta-cv-example.json
   ```

4. **Install CSV viewer extension** (recommended):
   - Install "Edit csv" or "Excel Viewer" extension in VS Code/VS Code Fork
   - **Edit CSV** is particularly recommended for its advanced CSV editing capabilities
   - Makes it easier to view and edit CSV files like `tracker.csv` and `requirements.csv`

### Step 2: Test with Minimal Configuration
1. **Use default rules**:
   ```bash
   cp rules/rules-default.json rules/user-rules.json
   ```

2. **Test with simple job**:
   - Use a basic job description
   - Check if system processes correctly
   - Verify output quality

3. **Gradually add complexity**:
   - Add custom preferences
   - Test with different job types
   - Monitor for issues

### Step 3: Check Content Libraries
1. **Verify meta content exists**:
   - Check meta CV file
   - Check meta cover letter file
   - Verify content quality

2. **Test content selection**:
   - Check relevance scores
   - Verify metadata
   - Test filtering

3. **Update content if needed**:
   - Add missing content
   - Improve existing content
   - Update metadata

### Step 4: Monitor System Performance
1. **Check resource usage**:
   - Monitor memory usage
   - Check disk space
   - Verify CPU usage

2. **Optimize if needed**:
   - Clean up old files
   - Optimize content libraries
   - Adjust quality thresholds

3. **Test performance**:
   - Process sample jobs
   - Measure processing time
   - Check output quality

## Getting Help

### Self-Help Resources
1. **Documentation**: Check relevant documentation sections
2. **Examples**: Review example files for reference
3. **Templates**: Use templates as starting points
4. **Community**: Check for community support

### Debugging Tools
1. **JSON Validators**: Online and command-line tools
2. **Markdown Validators**: Check generated content
3. **File System Tools**: Check permissions and structure
4. **Performance Monitors**: System resource monitoring

### When to Seek Help
1. **Persistent errors**: After trying all solutions
2. **System crashes**: Repeated failures
3. **Data loss**: Missing or corrupted files
4. **Performance issues**: Unacceptable slow performance

### Providing Information
When seeking help, provide:
1. **Error messages**: Exact error text
2. **System information**: OS, version, resources
3. **Configuration**: Relevant configuration files
4. **Steps to reproduce**: How to reproduce the issue
5. **Expected vs actual**: What should happen vs what happens
