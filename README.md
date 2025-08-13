# LinkedIn Job Search Automation

This project provides an automated workflow to streamline your LinkedIn job search, built using `n8n`. It helps you efficiently find relevant job postings, extract key information, and manage your applications by integrating with Google Drive and Google Sheets.

## Features:

* **Automated Job Search:** Automatically searches LinkedIn for jobs based on your specified criteria.
* **Customizable Filters:** Filter jobs by keywords, location, experience level, job type (full-time, part-time, contract, etc.), and "Easy Apply" option.
* **Resume Integration:** Reads your resume from Google Drive to potentially assist with future features (e.g., personalized cover letters - *this is a great potential future enhancement you can mention!*).
* **Google Sheets Integration:**
    * Reads search parameters from a Google Sheet.
    * Appends scraped job details (title, company, location, link, description, job ID, score) to another Google Sheet for easy tracking.
* **Scheduled Execution:** Configurable to run daily or at specific intervals.
* **Data Extraction:** Parses job HTML pages to extract crucial information like job title, company, location, job description, and direct application links.
* **Score Filtering:** (If applicable, based on your n8n workflow's "Score Filter" node) Filters jobs based on a defined score.

## How it Works:

The core of this project is an `n8n` workflow that orchestrates the following steps:

1.  **Trigger:** Can be initiated manually or on a schedule (e.g., daily at 5 PM).
2.  **Resume Download:** Fetches your resume (PDF) from Google Drive.
3.  **Search Parameters:** Reads job search criteria (keywords, location, experience level, etc.) from a designated Google Sheet.
4.  **URL Construction:** Dynamically builds LinkedIn job search URLs based on your criteria.
5.  **Job Fetching:** Makes HTTP requests to LinkedIn to retrieve job listings.
6.  **Link Extraction:** Extracts individual job posting links from the search results.
7.  **Job Page Parsing:** Visits each job page, extracts detailed information (title, company, description, apply link), and normalizes the data.
8.  **Data Storage:** Appends the extracted job details to a separate Google Sheet.
9.  **Filtering (Optional):** Applies a score filter to only include jobs that meet certain criteria (if configured).

## Getting Started:

### Prerequisites:

* An `n8n` instance (self-hosted or cloud).
* Google Drive account (for your resume).
* Google Sheets account (for search parameters and job tracking).

### Setup Steps:

1.  **Download the Workflow:** Clone this repository or download the `JOB Search - Linkedin.json` file.
2.  **Import into n8n:** Import the `.json` file into your `n8n` instance.
3.  **Configure Credentials:**
    * **Google Drive:** Set up your Google Drive OAuth2 API credentials in `n8n` and link your resume PDF.
    * **Google Sheets:** Set up your Google Sheets OAuth2 API credentials in `n8n` and link your search list and search automation Google Sheets.
4.  **Google Sheet Templates:** [Google Sheet Template](https://docs.google.com/spreadsheets/d/1G1t-50G0RwJPctUBEutuwJt83gV5N9WT) (or it will be included with the repository)
    * **Search List Template:** Create a Google Sheet with columns for `Keyword`, `Location`, `Experience Level`, `Remote`, `Job Type`, and `Easy Apply`. You can use this template: [link to your Google Sheet template - e.g., a public view-only link to the template you've already created/mentioned].
    * **Job Tracking Sheet:** Create another Google Sheet where the extracted job details will be appended. Ensure it has columns for `JobId`, `Title`, `Company`, `Location`, `link`, and `description`.
5.  **Activate Workflow:** Once configured, activate the workflow in `n8n`.

## Usage:

* Update your search criteria in the "Search List" Google Sheet.
* The workflow will automatically run based on its schedule (or you can trigger it manually).
* View the scraped job details in your "Job Tracking" Google Sheet.

## Future Enhancements:

* Automated cover letter generation based on resume and job description.
* Integration with other job boards.
* Notifications for new relevant jobs.
* More advanced scoring for job relevance.

## Contributing:

Feel free to fork this repository, open issues, and submit pull requests. Any contributions are welcome!

## License:

This project is open-source and available under the [MIT License](LICENSE).