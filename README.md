#!/bin/bash

# User-specific details
GITHUB_USERNAME="your-username"    # Replace with your GitHub username
REPO_NAME="your-github-profile"   # Use your username as the repository name for a profile repo
DESCRIPTION="My Professional GitHub Profile" 
VISIBILITY="public"                # Set 'private' for private repos

# Step 1: Create GitHub Repository
echo "Creating GitHub repository..."
gh repo create "$REPO_NAME" --description "$DESCRIPTION" --$VISIBILITY --confirm

# Step 2: Clone the Repository Locally
echo "Cloning the repository..."
git clone "https://github.com/$GITHUB_USERNAME/$REPO_NAME.git"
cd "$REPO_NAME" || exit

# Step 3: Add a README File
echo "Adding a README.md..."
cat > README.md <<EOL
# $GITHUB_USERNAME

## Welcome to My Professional GitHub Profile!
- **Experience:** 6+ years in IT Support & Application Development
- **Specializations:** Cloud Solutions, Cybersecurity, and Technical Support
- **Skills:** Azure, Intune, Okta, Jira, Microsoft Office 365
- **Certifications:** CPEH, CPTE, CompTIA Security+

Stay tuned for more updates and projects!
EOL

# Step 4: Commit Changes
git add README.md
git commit -m "Initial commit with README.md"

# Step 5: Push to GitHub
echo "Pushing changes to GitHub..."
git push -u origin main

# Completion Message
echo "GitHub profile repository '$REPO_NAME' has been successfully set up!"
