# Quick Setup Guide

## 1. Initial Setup
```bash
# Copy default rules to user rules
cp rules/rules-default.json rules/user-rules.json

# Copy meta examples to your personal files
cp meta/meta-cv-example.json meta/my-meta-cv.json
cp meta/meta-cover-letter-example.json meta/my-meta-cover-letter.json

# Copy tracker example to your personal tracker
cp tracker-example.csv tracker.csv
```

## 2. Create .gitignore File
Create a `.gitignore` file in the root directory to protect your personal data:
```bash
# Create .gitignore file
touch .gitignore
```

Add the following content to `.gitignore`:
```
# User-specific files
rules/user-rules.json
meta/my-meta-*.json

# Job application data (contains personal information)
jobs/*/

# Temporary files
*.tmp
*.temp
.DS_Store
Thumbs.db

# IDE files
.vscode/
.idea/
*.swp
*.swo

# Logs
*.log

# Backup files
*.bak
*.backup
```

## 3. Customize Your Files
- Edit `rules/user-rules.json` with your personal information
- Edit `meta/my-meta-cv.json` with your CV content
- Edit `meta/my-meta-cover-letter.json` with your cover letter content

## 4. Install VS Code Extensions (Recommended)
- **"Edit csv"** - Highly recommended for advanced CSV file editing capabilities
- "Excel Viewer" as alternative for CSV file viewing
- JSON extension for better JSON editing

## 5. Test the System
- Process a sample job using the instructions
- Generate a test CV and personal statement
- Review and adjust your rules as needed

## 6. Start Using
- Add job descriptions to process
- Generate targeted applications
- Track your progress in `tracker-example.csv` (copy to `tracker.csv` for your personal use)

## Next Steps
- Read the [Complete User Guide](docs/user-guide.md)
- Check the [Troubleshooting Guide](docs/troubleshooting.md) if you encounter issues
- Customize the system to your specific needs
