# Research Management System

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Usage](#usage)
- [Routes](#routes)
- [Database Models](#database-models)
- [Form Descriptions](#form-descriptions)
- [Template Descriptions](#template-descriptions)
- [Technologies Used](#technologies-used)

## Introduction
The Research Management System is a web application designed to manage and track journal and conference publications. It provides a user-friendly interface for users to log in, submit, view, and manage their research publications. The system also includes administrative features for managing user roles and sending notifications.

## Features
- User authentication and role management
- Submission of journal and conference publications
- Viewing and editing of publication entries
- PDF generation of publication data
- Email notifications to users
- Admin dashboard for managing entries and users

## Usage
To start using the application, run the following command:

```python
python app.py
```

The application will start running on `http://127.0.0.1:5000/`.

## Routes
### Authentication
- `/`: Login page
- `/login`: Login form processing

### User Pages
- `/home`: Home page
- `/unauthorised`: Unauthorized access page

### Admin Pages
- `/admin`: Admin dashboard
- `/admin_publication`: Admin publication management page
- `/entries`: View all journal and conference entries

### Journal Management
- `/journal`: Add a new journal entry
- `/edit_journal/<string:journal_doi>`: Edit a journal entry
- `/delete_journal/<string:journal_doi>`: Delete a journal entry
- `/show_entry/<string:journal_doi>`: Show details of a journal entry
- `/generate-pdf-journal`: Generate a PDF of all journal entries

### Conference Management
- `/conference`: Add a new conference entry
- `/edit_conference/<string:conf_url>`: Edit a conference entry
- `/delete_conference/<string:conf_url>`: Delete a conference entry
- `/show_conf_entry/<string:conf_url>`: Show details of a conference entry
- `/generate-pdf-conference`: Generate a PDF of all conference entries

### Notifications
- `/send_mail`: Send email notifications to all non-admin users

## Database Models
### USER_DETAIL
- `email`: User email (Primary Key)
- `roles`: User role (e.g., 'admin', 'user')

### JOURNALS
- `j_email`: User email
- `j_dop`: Date of publication
- `j_nat_inat`: National/International
- `j_ranking`: Ranking
- `j_broad_area`: Broad area
- `j_con_name`: Conference name
- `j_impf`: Impact factor
- `j_pap_tit`: Paper title
- `j_doi`: DOI (Primary Key)
- `j_authors`: Authors
- `j_volume`: Volume
- `j_issue`: Issue
- `j_page_n`: Page numbers
- `j_publisher`: Publisher
- `j_con_loc`: Conference location

### CONFERENCE
- `c_email`: User email
- `c_date`: Conference date
- `c_nat`: National/International
- `c_corerank`: Core ranking
- `c_pap_tit`: Paper title
- `c_short_name`: Short name
- `c_con_location`: Conference location
- `c_full_name`: Full name
- `c_url`: URL (Primary Key)
- `c_authors`: Authors
- `c_volume`: Volume
- `c_issue`: Issue
- `c_page_n`: Page numbers
- `c_publisher`: Publisher

## Form Descriptions
### LoginForm
- `email`: User email input
- `password`: User password input

### Journal Form (in `journal_page` and `edit_journal`)
- `publication-date`: Date of publication
- `national-international`: National or International status
- `ranking`: Ranking
- `broad-area`: Broad area of research
- `paper-title`: Paper title
- `conference-name`: Conference name
- `impact-factor`: Impact factor
- `conference-location`: Conference location
- `volume`: Volume number
- `issue`: Issue number
- `page-numbers`: Page numbers
- `doi`: Digital Object Identifier
- `publisher`: Publisher name
- `authors`: Authors

### Conference Form (in `conference` and `edit_conference`)
- `conference-date`: Date of the conference
- `type`: National or International status
- `corerank`: Core ranking
- `title`: Paper title
- `shortname`: Conference short name
- `location`: Conference location
- `fullname`: Conference full name
- `url`: Conference URL
- `authors`: Authors
- `volume`: Volume number
- `issue`: Issue number
- `pages`: Page numbers
- `publisher`: Publisher name

## Template Descriptions
### Authentication Templates
- `LoginPage.html`: Login form

### User Templates
- `HomePage.html`: Home page content
- `UnauthorizedAccess.html`: Unauthorized access message

### Admin Templates
- `AdminPage.html`: Admin dashboard content
- `AdminPublicationPage.html`: Admin publication management content
- `EntriesPage.html`: List of all journal and conference entries

### Journal Templates
- `JournalPage.html`: Form for adding or editing journal entries
- `ShowJournalPage.html`: Details of a specific journal entry

### Conference Templates
- `ConferencePage.html`: Form for adding or editing conference entries
- `ShowConferencePage.html`: Details of a specific conference entry

## Technologies Used
- **Flask**: Web framework
- **Flask-SQLAlchemy**: ORM for database interactions
- **SQLite**: Database
- **WTForms**: Form handling
- **smtplib**: Email sending
- **ReportLab**: PDF generation
- **HTML/CSS**: Front-end templating
