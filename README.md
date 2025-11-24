# Jenkins Portfolio - Setup Guide

This project demonstrates a portfolio website with Jenkins CI/CD integration.

## Portfolio Structure

- **Page 1**: About Me / Description page
- **Page 2**: Projects showcase
- Clean white background with black text
- Responsive design

## Running Locally

### Option 1: Using Python (Simplest)
```bash
# Navigate to project directory
cd "/Users/prathameshjadhav/Downloads/lab/jenkins protfoilo"

# Start a local server on port 8000
python3 -m http.server 8000
```

Then open: http://localhost:8000

### Option 2: Using Node.js
```bash
# Install http-server globally (one time)
npm install -g http-server

# Start server
http-server -p 8000
```

## Jenkins Setup - Local Installation

### Step 1: Install Jenkins

#### macOS (using Homebrew):
```bash
# Install Jenkins
brew install jenkins-lts

# Start Jenkins
brew services start jenkins-lts
```

#### Alternative - Using Docker:
```bash
# Run Jenkins in Docker container
docker run -d \
  --name jenkins \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

### Step 2: Access Jenkins

1. Open your browser and go to: http://localhost:8080
2. Get the initial admin password:
   ```bash
   # For Homebrew installation:
   cat ~/.jenkins/secrets/initialAdminPassword
   
   # For Docker installation:
   docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
   ```
3. Follow the setup wizard and install suggested plugins

### Step 3: Create a Jenkins Pipeline

1. Click "New Item"
2. Enter name: "Portfolio-Pipeline"
3. Select "Pipeline" and click OK
4. In the Pipeline section:
   - Definition: "Pipeline script from SCM" OR "Pipeline script"
   - If "Pipeline script", copy the content from Jenkinsfile
5. Click "Save"

### Step 4: Run the Pipeline

1. Click "Build Now"
2. Watch the pipeline execute through stages:
   - Checkout
   - Build
   - Test
   - Deploy
3. View console output for detailed logs

## Project Files

- `index.html` - Main portfolio page with navigation
- `styles.css` - Styling (white background, black text)
- `Jenkinsfile` - CI/CD pipeline configuration
- `README.md` - This file

## Pipeline Stages

1. **Checkout**: Prepares source code
2. **Build**: Creates build artifacts
3. **Test**: Validates HTML and CSS files exist
4. **Deploy**: Simulates deployment process

## Customization

- Edit `index.html` to update your personal information and projects
- Modify `styles.css` to change the design
- Update `Jenkinsfile` to add more pipeline stages

## Troubleshooting

### Jenkins not starting?
```bash
# Check if Jenkins is running
brew services list

# Restart Jenkins
brew services restart jenkins-lts
```

### Port already in use?
```bash
# Change the port in the Python command
python3 -m http.server 8001
```

## Next Steps

- Connect Jenkins to a Git repository
- Add automated testing scripts
- Set up webhooks for automatic builds
- Deploy to cloud platforms (AWS, Azure, etc.)

---

Created by Prathamesh Jadhav
