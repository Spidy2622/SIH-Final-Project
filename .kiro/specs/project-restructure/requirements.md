# Requirements Document

## Introduction

This document outlines the requirements for restructuring the SIH-Project to separate frontend and backend components into distinct directories with proper deployment configurations. The current project has a nested structure that makes deployment complex, and we need to reorganize it into a clean, deployable architecture.

## Requirements

### Requirement 1

**User Story:** As a developer, I want the frontend and backend to be in separate root-level directories, so that I can deploy them independently to different hosting services.

#### Acceptance Criteria

1. WHEN the project is restructured THEN the frontend SHALL be located in a `frontend/` directory at the root level
2. WHEN the project is restructured THEN the backend SHALL be located in a `backend/` directory at the root level
3. WHEN the directories are created THEN each SHALL contain its own package.json with appropriate scripts
4. WHEN the restructure is complete THEN the nested `project-bolt-sb1-udhsdu17` directory SHALL be removed

### Requirement 2

**User Story:** As a developer, I want proper build and deployment scripts, so that I can easily build and deploy both frontend and backend applications.

#### Acceptance Criteria

1. WHEN the frontend is restructured THEN it SHALL have build, dev, and preview scripts configured
2. WHEN the backend is restructured THEN it SHALL have dev, build, and start scripts configured
3. WHEN the root directory is updated THEN it SHALL contain a package.json with workspace scripts to manage both frontend and backend
4. WHEN scripts are configured THEN they SHALL allow running both applications simultaneously for development

### Requirement 3

**User Story:** As a developer, I want environment configuration files properly organized, so that I can manage different deployment environments.

#### Acceptance Criteria

1. WHEN the backend is restructured THEN the .env file SHALL be moved to the backend directory
2. WHEN environment files are organized THEN example .env files SHALL be provided for both frontend and backend
3. WHEN configuration is complete THEN the backend SHALL be configured to serve API routes with proper CORS settings
4. WHEN the frontend is configured THEN it SHALL have proper API endpoint configuration for different environments

### Requirement 4

**User Story:** As a developer, I want the project to maintain all existing functionality, so that no features are lost during restructuring.

#### Acceptance Criteria

1. WHEN the restructure is complete THEN all React components SHALL be preserved in the frontend directory
2. WHEN the restructure is complete THEN all Express routes and models SHALL be preserved in the backend directory
3. WHEN the applications are started THEN the frontend SHALL successfully connect to the backend API
4. WHEN testing the application THEN all existing features SHALL work as before

### Requirement 5

**User Story:** As a developer, I want clear documentation and README files, so that I can understand how to run and deploy the restructured project.

#### Acceptance Criteria

1. WHEN the restructure is complete THEN the root README SHALL contain setup and deployment instructions
2. WHEN documentation is created THEN each subdirectory SHALL have its own README with specific instructions
3. WHEN documentation is provided THEN it SHALL include development, build, and deployment commands
4. WHEN instructions are written THEN they SHALL specify required Node.js versions and dependencies