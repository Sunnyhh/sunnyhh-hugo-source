#!/bin/bash

# Navigate to the website source directory
cd /Users/sunny/Library/CloudStorage/OneDrive-Personal/GitHub/website-source

echo "🚀 Starting Hugo deployment..."

# Build the site
echo "📦 Building Hugo site..."
hugo

# Check if build was successful
if [ $? -ne 0 ]; then
    echo "❌ Hugo build failed!"
    exit 1
fi

# Navigate to public directory
echo "📂 Navigating to public directory..."
cd public

# Initialize git if needed
if [ ! -d ".git" ]; then
    echo "🔧 Initializing git in public directory..."
    git init
    git remote add origin git@github.com:Sunnyhh/sunnyhh.github.io.git
fi

# Add and commit changes
echo "📝 Adding and committing changes..."
git add .
git commit -m "Deploy Hugo site - $(date '+%Y-%m-%d %H:%M:%S')" || echo "No changes to commit"

# Push to GitHub Pages repository
echo "🌐 Pushing to GitHub Pages..."
git push origin main --force

# Check if push was successful
if [ $? -eq 0 ]; then
    echo "✅ Deployment successful!"
    echo "🌍 Your site should be live at: https://sunnyhh.github.io"
else
    echo "❌ Deployment failed!"
    exit 1
fi

# Return to project root
cd ..

echo "🎉 Deployment complete!"