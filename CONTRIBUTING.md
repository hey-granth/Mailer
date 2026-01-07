# Contributing to Mailer

Thank you for your interest in contributing to Mailer. This document provides guidelines and instructions for contributing to the project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Contribution Workflow](#contribution-workflow)
- [Coding Standards](#coding-standards)
- [Testing Guidelines](#testing-guidelines)
- [Pull Request Process](#pull-request-process)
- [Reporting Issues](#reporting-issues)

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment. We expect all contributors to:

- Use welcoming and inclusive language
- Respect differing viewpoints and experiences
- Accept constructive criticism gracefully
- Focus on what is best for the community
- Show empathy towards other community members

## Getting Started

### Prerequisites

Before contributing, ensure you have:

- Python 3.7 or higher installed
- Git version control
- A GitHub account
- Google Chrome browser
- Basic understanding of Selenium and web scraping
- Familiarity with email protocols and SMTP

### Finding Ways to Contribute

You can contribute in several ways:

- Fix bugs reported in Issues
- Implement new features from the roadmap
- Improve documentation
- Add test coverage
- Optimize performance
- Enhance error handling
- Add support for additional email providers

## Development Setup

1. Fork the repository on GitHub

2. Clone your fork locally:
```bash
git clone https://github.com/your-username/Mailer.git
cd Mailer
```

3. Add the upstream repository:
```bash
git remote add upstream https://github.com/original-owner/Mailer.git
```

4. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

5. Install dependencies:
```bash
pip install -r requirements.txt
```

6. Create a new branch for your work:
```bash
git checkout -b feature/your-feature-name
```

## Contribution Workflow

### 1. Sync Your Fork

Before starting work, sync your fork with the upstream repository:

```bash
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
```

### 2. Create a Feature Branch

```bash
git checkout -b feature/descriptive-name
```

Branch naming conventions:
- `feature/` for new features
- `bugfix/` for bug fixes
- `docs/` for documentation updates
- `refactor/` for code refactoring
- `test/` for adding tests

### 3. Make Your Changes

- Write clean, readable code
- Follow the coding standards outlined below
- Add comments for complex logic
- Update documentation as needed

### 4. Commit Your Changes

Write clear, descriptive commit messages:

```bash
git add .
git commit -m "Add feature: brief description"
```

Commit message format:
```
<type>: <subject>

<body>

<footer>
```

Types:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

Example:
```
feat: Add support for Outlook email provider

Implemented SMTP configuration for Outlook accounts.
Added validation for Outlook-specific credentials.
Updated documentation with Outlook setup instructions.

Closes #123
```

### 5. Push to Your Fork

```bash
git push origin feature/your-feature-name
```

### 6. Submit a Pull Request

- Go to your fork on GitHub
- Click "New Pull Request"
- Select your feature branch
- Fill out the PR template completely
- Link any related issues

## Coding Standards

### Python Style Guide

Follow PEP 8 guidelines with these specifics:

- Use 4 spaces for indentation (no tabs)
- Maximum line length: 100 characters
- Use descriptive variable names
- Add docstrings to all functions and classes

Example:

```python
def generate_email_address(first_name, last_name, domain):
    """
    Generate an email address based on name components and domain.
    
    Args:
        first_name (str): First name of the recipient
        last_name (str): Last name of the recipient
        domain (str): Email domain (e.g., 'company.com')
    
    Returns:
        str: Formatted email address
    
    Raises:
        ValueError: If any parameter is empty or invalid
    """
    if not all([first_name, last_name, domain]):
        raise ValueError("All parameters must be non-empty strings")
    
    return f"{first_name.lower()}.{last_name.lower()}@{domain}"
```

### Code Organization

- Keep functions focused and single-purpose
- Limit function length to 50 lines when possible
- Use meaningful function and variable names
- Group related functions together
- Add blank lines between logical sections

### Error Handling

Always implement proper error handling:

```python
try:
    result = risky_operation()
except SpecificException as e:
    logger.error(f"Operation failed: {e}")
    # Handle gracefully
finally:
    cleanup_resources()
```

### Configuration Management

- Never commit sensitive data (passwords, API keys)
- Use environment variables for configuration
- Provide example configuration files (e.g., `.env.example`)
- Document all configuration options

## Testing Guidelines

### Writing Tests

While the project currently lacks comprehensive tests, contributors are encouraged to add them:

1. Create a `tests/` directory if it doesn't exist
2. Name test files with `test_` prefix
3. Use descriptive test function names
4. Test both success and failure cases

Example test structure:

```python
import unittest
from send_email import generate_contacts

class TestEmailGeneration(unittest.TestCase):
    
    def test_generate_contacts_valid_csv(self):
        """Test contact generation with valid CSV input"""
        # Test implementation
        pass
    
    def test_generate_contacts_empty_csv(self):
        """Test handling of empty CSV file"""
        # Test implementation
        pass
    
    def test_generate_contacts_malformed_names(self):
        """Test handling of malformed name entries"""
        # Test implementation
        pass
```

### Running Tests

```bash
python -m unittest discover tests/
```

## Pull Request Process

### Before Submitting

- Ensure your code follows the coding standards
- Update documentation to reflect your changes
- Add or update tests as appropriate
- Verify all tests pass locally
- Rebase your branch on the latest main branch

### PR Description Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Code refactoring
- [ ] Performance improvement

## Changes Made
- Change 1
- Change 2
- Change 3

## Testing
Describe testing performed

## Related Issues
Closes #issue_number

## Screenshots (if applicable)
Add screenshots for UI changes

## Checklist
- [ ] Code follows project style guidelines
- [ ] Self-review completed
- [ ] Comments added for complex code
- [ ] Documentation updated
- [ ] No new warnings generated
- [ ] Tests added/updated
- [ ] All tests passing
```

### Review Process

1. Maintainers will review your PR within 5 business days
2. Address any requested changes
3. Once approved, a maintainer will merge your PR
4. Your contribution will be credited in the release notes

## Reporting Issues

### Bug Reports

When reporting bugs, include:

- Clear, descriptive title
- Steps to reproduce the issue
- Expected behavior
- Actual behavior
- Environment details (OS, Python version, Chrome version)
- Error messages and stack traces
- Screenshots if applicable

### Feature Requests

For feature requests, provide:

- Clear description of the proposed feature
- Use case and motivation
- Potential implementation approach
- Any relevant examples or references

### Issue Template

```markdown
## Issue Type
- [ ] Bug Report
- [ ] Feature Request
- [ ] Documentation Issue

## Description
Clear description of the issue or request

## Steps to Reproduce (for bugs)
1. Step 1
2. Step 2
3. Step 3

## Expected Behavior
What should happen

## Actual Behavior
What actually happens

## Environment
- OS: 
- Python Version: 
- Chrome Version: 
- ChromeDriver Version: 

## Additional Context
Any other relevant information
```

## Development Best Practices

### Security Considerations

- Never log sensitive information (passwords, tokens)
- Validate all user inputs
- Use parameterized queries where applicable
- Keep dependencies updated
- Follow OWASP security guidelines

### Performance Optimization

- Minimize unnecessary API calls
- Implement appropriate rate limiting
- Use efficient data structures
- Profile code for bottlenecks
- Cache results when appropriate

### Documentation

- Update README.md for user-facing changes
- Add inline comments for complex logic
- Document all public APIs
- Include usage examples
- Keep documentation in sync with code

## Questions and Support

If you have questions about contributing:

- Check existing documentation
- Search closed issues and PRs
- Open a new issue with the "question" label
- Reach out to maintainers

## Recognition

Contributors will be recognized in:

- Project README
- Release notes
- GitHub contributors page

Thank you for contributing to Mailer and helping improve the project for everyone.
