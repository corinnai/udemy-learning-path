- [Jira](#jira)
- [Key Agile Terms you’ll Find in JIRA](#key-agile-terms-youll-find-in-jira)
- [Jira Terms](#jira-terms)
- [Team-Managed Projects vs Company-Managed Projects](#team-managed-projects-vs-company-managed-projects)
  - [Company-Managed Projects](#company-managed-projects)
  - [Team-Managed Projects](#team-managed-projects)
  - [Team-managed projects](#team-managed-projects-1)
    - [Step 1: Log in to Jira](#step-1-log-in-to-jira)
    - [Step 2: Go to the Projects Page](#step-2-go-to-the-projects-page)
    - [Step 3: Choose Project Type](#step-3-choose-project-type)
    - [Step 4: Select a Project Template](#step-4-select-a-project-template)
    - [Step 5: Configure Project Details](#step-5-configure-project-details)
    - [Step 6: Create the Project](#step-6-create-the-project)
    - [Step 7: Customize Your Project (Optional)](#step-7-customize-your-project-optional)
    - [Step 8: Invite Team Members](#step-8-invite-team-members)
    - [Step 9: Start Using Your Project](#step-9-start-using-your-project)
- [Creating a Company-Managed Project](#creating-a-company-managed-project)
  - [Step 1: Log In to Jira](#step-1-log-in-to-jira-1)
  - [Step 2: Access the Project Creation Screen](#step-2-access-the-project-creation-screen)
  - [Step 3: Select the Project Type](#step-3-select-the-project-type)
  - [Step 4: Choose a Project Template](#step-4-choose-a-project-template)
  - [Step 5: Configure Project Details](#step-5-configure-project-details-1)
  - [Step 6: Set Project Permissions (Optional)](#step-6-set-project-permissions-optional)
  - [Step 7: Finalize Project Creation](#step-7-finalize-project-creation)
  - [Step 8: Configure Additional Project Settings (Optional)](#step-8-configure-additional-project-settings-optional)
  - [Step 9: Invite Team Members](#step-9-invite-team-members)
- [Jira's Administrative Back End](#jiras-administrative-back-end)
- [Company-Managed Project Administration](#company-managed-project-administration)
- [Workflows](#workflows)
- [Schemes](#schemes)
  - [1. Permission Scheme](#1-permission-scheme)
  - [2. Notification Scheme](#2-notification-scheme)
  - [3. Workflow Scheme](#3-workflow-scheme)
  - [4. Issue Type Scheme](#4-issue-type-scheme)
  - [5. Screen Scheme](#5-screen-scheme)
  - [6. Issue Type Screen Scheme](#6-issue-type-screen-scheme)
  - [7. Field Configuration Scheme](#7-field-configuration-scheme)
  - [8. Issue Security Scheme](#8-issue-security-scheme)
    - [How Schemes Work Together](#how-schemes-work-together)
- [Confluence Cloud](#confluence-cloud)
  - [Confluence](#confluence)
  - [Confluence vs. Jira: Simplified Comparison](#confluence-vs-jira-simplified-comparison)
    - [Purpose](#purpose)
    - [Main Use](#main-use)
    - [Key Features](#key-features)
    - [Integration](#integration)
    - [Who Uses It](#who-uses-it)
    - [Summary](#summary)
  - [Confluence : Using Personal Spaces](#confluence--using-personal-spaces)
    - [1. Understanding Personal Spaces](#1-understanding-personal-spaces)
    - [2. Creating a Personal Space](#2-creating-a-personal-space)
    - [3. Organizing Content](#3-organizing-content)
    - [4. Creating Pages](#4-creating-pages)
    - [5. Managing Visibility](#5-managing-visibility)
    - [6. Deleting a Personal Space](#6-deleting-a-personal-space)
    - [7. Best Practices](#7-best-practices)
  - [Team Spaces vs. Personal Spaces in Confluence](#team-spaces-vs-personal-spaces-in-confluence)
    - [Purpose](#purpose-1)
    - [Accessibility](#accessibility)
    - [Typical Use Cases](#typical-use-cases)
    - [Permissions](#permissions)
    - [Content Organization](#content-organization)
    - [Ideal For](#ideal-for)
    - [Summary](#summary-1)
  - [Confluence : Using Team Spaces:](#confluence--using-team-spaces)
    - [1. Understanding Team Spaces](#1-understanding-team-spaces)
    - [2. Creating a Team Space](#2-creating-a-team-space)
    - [3. Managing Permissions](#3-managing-permissions)
    - [4. Organizing Content](#4-organizing-content)
    - [5. Collaboration Features](#5-collaboration-features)
    - [6. Coordination Tools](#6-coordination-tools)
    - [7. Best Practices](#7-best-practices-1)



# Jira 
- JIRA is a project management and issue-tracking tool


# Key Agile Terms you’ll Find in JIRA
- Stories and Epics
  -  **User Story** : As a `<type of user>`, I want `<some goal>` so that `<some reason>`.
  - **Epics**: An epic is a story that is too big for a single sprint. It’s broken down into multiple user stories. When those are done, the epic is complete.

# Jira Terms 
-  Issues and Projects
   -  Issues are containers for fields, and fields 
hold all of your data.
        - Example of fields:
          - description
          - summary
          - due date
          - attachments
   - Projects : Issues live inside your jira projects
  

# Team-Managed Projects vs Company-Managed Projects

## Company-Managed Projects
- Global entities
- Must be Jira admin to create
- More complicated to set up and maintain
## Team-Managed Projects 
- Project scope entities
- No special permissions to create
- Fast and easy to set up and maintain

## Team-managed projects
### Step 1: Log in to Jira
- Go to your Jira instance and log in with your credentials.
### Step 2: Go to the Projects Page
- In the left sidebar, select **Projects**.
- Click on **Create project** at the top.
### Step 3: Choose Project Type
- In the "Create project" window, you’ll see options for **Team-managed** and **Company-managed projects**.
- Select Team-managed project.
### Step 4: Select a Project Template
- Choose the template that best suits your project’s needs, such as **Kanban**, **Scrum**, or **Bug Tracking**.
- Each template has different settings tailored for different types of work.
### Step 5: Configure Project Details
- Enter the **Project name**.
- Jira will automatically generate a **Project key**, which you can customize if desired (3–4 character identifier).
- Choose a **project lead** if needed. The default will be your account if you are the creator.
### Step 6: Create the Project
- Click on **Create** or **Create project** to finalize the creation.
- Jira will set up the project based on the template you chose, creating sample tasks and workflows if necessary.
### Step 7: Customize Your Project (Optional)
- Once created, you can customize project settings, including **columns** (in Kanban) or **sprints** (in Scrum).
- Set permissions for your team members if required.
### Step 8: Invite Team Members
- Under the **People** section, add team members by entering their emails or usernames.
- Assign them roles if needed (e.g., admin, member).
### Step 9: Start Using Your Project
- Begin creating **issues, tasks**, or **epics** as needed.
- Track progress, set priorities, and use the board to manage tasks.


# Creating a Company-Managed Project
## Step 1: Log In to Jira
1. Open your browser and navigate to your Jira instance.
2. Log in using your credentials.

## Step 2: Access the Project Creation Screen
1. From the Jira dashboard, click on **Projects** in the top navigation menu.
2. Select **Create Project** from the dropdown, or find the **Create project** button if visible.

## Step 3: Select the Project Type
1. You’ll see options for different types of projects.
2. Choose **Company-managed project**. This type requires Jira admin permissions and is used for projects with more complex configurations.

## Step 4: Choose a Project Template
1. Jira provides various templates depending on the type of work you’ll be managing. Common templates include **Scrum** (for iterative development), **Kanban** (for continuous flow), or **Service Management**.
2. Select the template that best suits your project needs.
3. Click **Use template** once you've selected your desired template.

## Step 5: Configure Project Details
1. Enter a **Project name**. This is the name that will appear across Jira.
2. Specify a **Project key** (a unique identifier used for task IDs within the project). Jira usually auto-generates one, but you can customize it.
3. If relevant, set a **Project lead** (this is typically the main point of contact or project owner).

## Step 6: Set Project Permissions (Optional)
1. If you want to configure access levels, you can adjust project permissions now or leave the default settings.
2. Permissions in a Company-managed project can be more complex and allow for custom settings.

## Step 7: Finalize Project Creation
1. Review your settings to ensure accuracy.
2. Click **Create** to finalize the creation of your Company-managed project.

## Step 8: Configure Additional Project Settings (Optional)
1. Once the project is created, you’ll be taken to the project’s main page.
2. If needed, configure additional settings, such as workflows, issue types, and permissions.
3. Access these settings through **Project settings** on the left sidebar.

## Step 9: Invite Team Members
1. Under **People** in the Project settings, add users to the project and assign roles.
2. This step ensures the right team members have access to the project and its tasks.


# Jira's Administrative Back End
- The Jira administrative back end, also known as the Jira Administration interface, is where administrators can manage and configure various aspects of Jira to align with organizational needs.

1. **User Management**: Add/remove users, assign roles, and set permissions.
2. **Project Configuration**: Create and configure projects, set access levels, and apply custom settings.
3. **Permissions and Notifications**: Control who can do what within Jira and manage notification settings.
4. **Custom Fields and Screens**: Set up fields for data collection and control what fields are shown on issue screens.
5. **Workflows**: Design workflows that define how issues move through statuses.
6. **Automation and Add-Ons**: Set up automation rules for repetitive tasks and install add-ons for additional functionality.
7. **Reports and Dashboards**: Create custom reports and dashboards for tracking progress.


# Company-Managed Project Administration
1. **Roles and Permissions**: Assign users to roles and control their access to project actions.
2. **Issue Types and Fields**: Define specific issue types (e.g., tasks, bugs) and add custom fields for project data.
3. **Workflows**: Create or apply workflows to manage how tasks move through stages in the project.
4. **Boards and Agile Tools**: Set up Scrum or Kanban boards, customize columns, and manage backlog.
5. **Components and Versions**: Organize issues by components (e.g., Frontend) and track progress with versioning.
6. **Reports and Automation**: Generate reports and automate repetitive tasks to improve efficiency.

---

# Workflows
1. **Statuses**: Define stages in the process, such as “To Do,” “In Progress,” and “Done.”
2. **Transitions**: Set up actions to move issues from one status to another.
3. **Conditions and Validators**: Control who can transition issues and ensure required fields are filled.
4. **Post Functions**: Automate tasks after transitions, like assigning issues or updating fields.
5. **Customization**: Use the workflow designer to create workflows tailored to your team’s needs.





# Schemes

## 1. Permission Scheme
- **Purpose**: Controls what users can do in a project (e.g., create or edit issues).
- **Use**: Assigns permissions to roles like Admin or Developer.
  
## 2. Notification Scheme
- **Purpose**: Decides who gets notified about issue updates.
- **Use**: Configures alerts based on user roles and events.

## 3. Workflow Scheme
- **Purpose**: Links workflows to different issue types.
- **Use**: Allows different processes for bugs, tasks, etc.

## 4. Issue Type Scheme
- **Purpose**: Defines the types of issues in a project (e.g., Bug, Task).
- **Use**: Ensures consistent issue types across projects.

## 5. Screen Scheme
- **Purpose**: Controls which fields show on different screens (e.g., create, edit).
- **Use**: Tailors screens for each action.

## 6. Issue Type Screen Scheme
- **Purpose**: Links screen schemes to specific issue types.
- **Use**: Customizes layouts for different issue types.

## 7. Field Configuration Scheme
- **Purpose**: Sets field behaviors (e.g., required or hidden).
- **Use**: Customizes field settings for each issue type.

## 8. Issue Security Scheme
- **Purpose**: Limits who can see certain issues.
- **Use**: Adds confidentiality for sensitive issues.


### How Schemes Work Together
- **Reusable**: Schemes can be used in multiple projects for consistency.
- **Centralized Control**: Changes to a scheme affect all projects using it.
- **Customization**: Each scheme type covers a specific aspect, making it easy to adapt Jira to team needs.


# Confluence Cloud

## Confluence 
- a wiki application ( a wikipedia - probably the most popular wiki app)
- Confluence is a collaboration and knowledge-sharing tool developed by Atlassian. It’s widely used by teams and organizations to create, organize, and share content in a centralized, accessible platform

## Confluence vs. Jira: Simplified Comparison

---

### Purpose
- **Confluence**: A collaboration and documentation tool, mainly used for creating, organizing, and sharing content like project notes, documentation, and knowledge bases.
- **Jira**: A project management tool, primarily used for tracking tasks, issues, and workflows, especially in software development.

### Main Use
- **Confluence**: Used to document and share information. Ideal for project documentation, meeting notes, knowledge sharing, and team collaboration.
- **Jira**: Used to manage and track work. Ideal for planning, assigning, and tracking tasks or issues within a project.

### Key Features
- **Confluence**: Pages, spaces, rich text editing, templates, and collaboration features like commenting and co-editing.
- **Jira**: Issue tracking, boards (Scrum/Kanban), workflows, task assignments, and progress tracking.

### Integration
- **Confluence**: Integrates with Jira to display and link Jira issues within documentation.
- **Jira**: Integrates with Confluence for easy access to related project documentation.

### Who Uses It
- **Confluence**: Typically used by all team members for knowledge sharing and documentation.
- **Jira**: Typically used by project managers, developers, and teams responsible for tracking project progress.

### Summary
- **Confluence = Documentation and Collaboration**
- **Jira = Project Tracking and Issue Management**


## Confluence : Using Personal Spaces 

### 1. Understanding Personal Spaces
- **Definition**: A private area for individual notes, drafts, or personal planning.
- **Purpose**: Ideal for storing information that doesn’t need to be shared with others.

### 2. Creating a Personal Space
- **Steps**:
  1. Go to your **Profile** menu.
  2. Select **Add Personal Space**.
  3. Customize the name and permissions.
- **Permissions**: By default, it's private, but you can share it with specific people.

### 3. Organizing Content
- **Structure**: Organize pages and sub-pages in a hierarchy.
- **Home Page**: Use as a central location with links to important content.

### 4. Creating Pages
- **Add Content**: Create pages for notes, tasks, and other documents.
- **Templates**: Use Confluence templates to structure content.
- **Editing**: Includes rich text, attachments, and macros.

### 5. Managing Visibility
- **Privacy**: Keep your space private or share specific pages.
- **Page Permissions**: Set individual permissions for pages within the space.

### 6. Deleting a Personal Space
- **Steps**:
  1. Go to **Space Settings**.
  2. Select **Delete Space** (backup important info first).

### 7. Best Practices
- **Organize Regularly**: Keep content easy to navigate.
- **Use for Drafts**: Ideal for drafting before sharing in team spaces.
- **Control Sensitive Info**: Limit visibility for private content.


## Team Spaces vs. Personal Spaces in Confluence

### Purpose
- **Team Spaces**: Shared areas designed for collaboration. Used for team projects, shared documentation, and group communication.
- **Personal Spaces**: Private or semi-private areas for individual work, notes, or drafts that may not need to be shared with the whole team.

### Accessibility
- **Team Spaces**: Accessible to all team members or specific groups, depending on permissions set by space administrators.
- **Personal Spaces**: Accessible only to the individual by default, but can be shared with specific people if desired.

### Typical Use Cases
- **Team Spaces**:
  - Project documentation
  - Meeting notes and agendas
  - Team announcements and updates
  - Collaborative content creation

- **Personal Spaces**:
  - Private notes and drafts
  - Personal project planning
  - Testing or experimenting with content
  - Content not ready for team sharing

### Permissions
- **Team Spaces**: Managed by space admins who can control access and editing rights for different users or groups.
- **Personal Spaces**: Managed by the individual, who can decide whether to keep it private or share specific pages with others.

### Content Organization
- **Team Spaces**: Structured with organized pages and sub-pages to support group access and navigation.
- **Personal Spaces**: Organized based on individual preferences, often with fewer hierarchical structures since they are for personal use.

### Ideal For
- **Team Spaces**: Team collaboration, shared resources, and centralized documentation for group access.
- **Personal Spaces**: Individual work, private notes, and content not yet ready to be shared.

---

### Summary
- **Team Spaces**: Best for collaborative, shared content across a team.
- **Personal Spaces**: Best for individual work and private documentation.



## Confluence : Using Team Spaces:

### 1. Understanding Team Spaces
- **Definition**: Shared areas for team collaboration on projects and documents.
- **Purpose**: Centralizes information, allowing teams to share updates and work together in real time.

### 2. Creating a Team Space
- **Steps**:
  1. Go to **Spaces** > **Create a Space** > Choose "Team Space".
  2. Name the space and add a description if needed.
- **Customization**: Customize the homepage with important links and updates.

### 3. Managing Permissions
- **Set Permissions**: Control who can view, edit, or comment.
- **Roles**: Assign roles like Space Admin to manage settings and permissions.

### 4. Organizing Content
- **Pages and Sub-pages**: Organize content hierarchically.
- **Templates**: Use templates for consistent layouts (e.g., meeting notes).
- **Labels**: Add labels to improve searchability.

### 5. Collaboration Features
- **Real-Time Editing**: Team members can edit pages together.
- **Comments and Mentions**: Use comments and `@mentions` to communicate.
- **Notifications**: Receive updates on changes to watched pages.

### 6. Coordination Tools
- **Tasks**: Assign tasks within pages to track action items.
- **Blogs**: Share announcements or updates within the team space.
- **Calendars and Macros**: Track deadlines and add dynamic content (e.g., Jira issues).

### 7. Best Practices
- **Organize Content**: Keep pages structured for easy access.
- **Encourage Collaboration**: Use comments, mentions, and shared editing.
- **Use Templates**: Standardize pages for consistency.


