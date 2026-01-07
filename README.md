# Mailer

A Python-based automation tool for scraping LinkedIn company employee names and sending personalized outreach emails. This tool streamlines the process of collecting contact information from LinkedIn company pages and sending customized email campaigns.

## Overview

Mailer automates two primary workflows:

1. **LinkedIn Scraping**: Extracts employee names from a company's LinkedIn people page using Selenium WebDriver
2. **Email Outreach**: Generates email addresses based on company naming conventions and sends personalized emails to prospects

## Features

- Automated LinkedIn profile scraping with configurable limits
- CSV export of collected names
- Customizable email templates with dynamic content
- Batch email sending with error handling
- Support for company-specific email format patterns
- Chrome browser automation with headless mode support

## Prerequisites

- Python 3.7 or higher
- Google Chrome browser
- ChromeDriver (included in repository)
- Gmail account with App Password enabled

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/Mailer.git
cd Mailer
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

3. Ensure ChromeDriver is executable:
```bash
chmod +x chromedriver
```

## Configuration

### Email Setup

Before running the tool, you need to configure your Gmail account:

1. Enable 2-Factor Authentication on your Google Account
2. Generate an App Password:
   - Go to Google Account Settings
   - Security > 2-Step Verification > App Passwords
   - Generate a new app password for "Mail"
3. Keep this password ready for when the script prompts you

### Company Email Template

Modify the `company_emails_template` function in `send_email.py` to match the target company's email format:

```python
def company_emails_template(first_name, last_name):
    return f"{first_name}.{last_name}@company.com"
```

Common patterns include:
- `first.last@company.com`
- `firstlast@company.com`
- `first_last@company.com`
- `flast@company.com`

## Usage

### Basic Workflow

1. Run the main script:
```bash
python main.py
```

2. Follow the interactive prompts:
   - Enter the LinkedIn company people page URL
   - Specify maximum number of names to scrape
   - Log into LinkedIn manually when the browser opens
   - Wait for scraping to complete
   - Choose whether to send emails

3. If sending emails, provide:
   - Your email address
   - Your Google App Password
   - Your name
   - Position you're applying for
   - Company name
   - Email subject
   - Resume link

### LinkedIn URL Format

The LinkedIn company people page URL should follow this format:
```
https://www.linkedin.com/company/{company-name}/people/
```

### Output

- A CSV file named `{company_name}_names.csv` containing scraped names
- Email delivery confirmations or error messages

## Project Structure

```
Mailer/
├── app.py                  # LinkedIn scraping logic
├── main.py                 # Entry point and driver configuration
├── send_email.py           # Email generation and sending logic
├── email_template.py       # HTML email template
├── requirements.txt        # Python dependencies
├── chromedriver.exe        # Chrome WebDriver binary
└── cookies/                # Browser session data (auto-generated)
```

## Core Components

### app.py

Handles LinkedIn scraping:
- Scrolls through company people page
- Extracts employee names using Selenium
- Exports results to CSV

### send_email.py

Manages email operations:
- Generates email addresses from names
- Configures email client
- Sends batch emails with error handling

### email_template.py

Defines the HTML email template with placeholders for:
- Recipient name
- Company name
- Position
- Resume link
- Applicant information

## Dependencies

Key dependencies include:

- `selenium`: Web browser automation
- `Notipyer`: Email sending functionality
- `webdriver-manager`: ChromeDriver management
- `requests`: HTTP library
- `python-dotenv`: Environment variable management

See `requirements.txt` for complete list.

## Important Notes

### Legal and Ethical Considerations

- Ensure compliance with LinkedIn's Terms of Service
- Respect data privacy regulations (GDPR, CCPA, etc.)
- Obtain proper consent before sending unsolicited emails
- Use responsibly and ethically
- Consider rate limiting to avoid being flagged as spam

### Technical Limitations

- Requires manual LinkedIn login (cannot automate authentication)
- Scraping speed limited by page load times and scroll delays
- Email format guessing may result in bounced emails
- Chrome browser must be installed on the system

### Best Practices

- Test with small batches first
- Verify email format accuracy before bulk sending
- Personalize email content for better response rates
- Monitor email deliverability and bounce rates
- Keep ChromeDriver updated with your Chrome version

## Troubleshooting

### ChromeDriver Issues

If you encounter ChromeDriver errors:
```bash
# Download the correct version for your Chrome browser
# from https://chromedriver.chromium.org/
```

### LinkedIn Login Issues

- Ensure you're logged into LinkedIn before scraping
- Check if LinkedIn requires CAPTCHA verification
- Try increasing sleep time in `app.py` if elements don't load

### Email Sending Failures

- Verify App Password is correct
- Check Gmail sending limits (500 emails/day for free accounts)
- Ensure recipient email format is valid
- Review spam filter settings

## License

This project is provided as-is for educational purposes. Users are responsible for ensuring compliance with all applicable laws and terms of service.

## Disclaimer

This tool is intended for legitimate networking and job application purposes only. The authors are not responsible for misuse or any violations of third-party terms of service. Always respect privacy, obtain consent, and follow applicable regulations when collecting and using personal data.
