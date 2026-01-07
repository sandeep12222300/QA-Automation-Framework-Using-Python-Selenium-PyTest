# QA Automation Framework Using Python, Selenium & PyTest

A robust and scalable test automation framework built with Python, Selenium WebDriver, and PyTest for web application testing. This framework follows the Page Object Model (POM) design pattern to ensure maintainable and reusable test code.

## Features

- **Page Object Model (POM)**: Organized structure with separate page objects for better code maintainability
- **PyTest Framework**: Powerful test framework with fixtures and detailed reporting
- **Selenium WebDriver**: Cross-browser automation support
- **WebDriver Manager**: Automatic browser driver management (no manual driver downloads needed)
- **HTML Reports**: Generates detailed HTML test reports using pytest-html
- **Modular Design**: Easy to extend with new test cases and page objects

## Project Structure

```
QA-Automation-Framework-Using-Python-Selenium-PyTest/
│
├── pages/                      # Page Object Model classes
│   └── login_page.py          # Login page object with locators and methods
│
├── tests/                      # Test cases
│   └── test_login.py          # Login functionality test cases
│
├── reports/                    # Generated test reports
│
├── conftest.py                # PyTest configuration and fixtures
├── requirements.txt           # Project dependencies
├── LICENSE                    # MIT License
└── README.md                  # Project documentation
```

## Prerequisites

- Python 3.7 or higher
- pip (Python package installer)
- Chrome browser (for running tests)

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/sandeep12222300/QA-Automation-Framework-Using-Python-Selenium-PyTest.git
   cd QA-Automation-Framework-Using-Python-Selenium-PyTest
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment:**
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

4. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## Technologies Used

- **Python**: Programming language
- **Selenium 4.39.0**: Web automation framework
- **PyTest 8.0.0**: Testing framework
- **pytest-html 4.1.1**: HTML report generation
- **webdriver-manager 4.0.1**: Automatic browser driver management

## Usage

### Running Tests

Run all tests:
```bash
pytest
```

Run tests with verbose output:
```bash
pytest -v
```

Run specific test file:
```bash
pytest tests/test_login.py
```

Run specific test function:
```bash
pytest tests/test_login.py::test_valid_login
```

Generate HTML report:
```bash
pytest --html=reports/report.html
```

Run tests with detailed output and HTML report:
```bash
pytest -v --html=reports/report.html --self-contained-html
```

### Writing New Tests

1. Create a new page object in the `pages/` directory following the POM pattern
2. Add test cases in the `tests/` directory
3. Use the `browser` fixture provided in `conftest.py` for WebDriver instance

Example test structure:
```python
from pages.your_page import YourPage

def test_example(browser):
    page = YourPage(browser)
    page.open()
    # Your test steps here
    assert expected_result == actual_result
```

## Page Object Model (POM)

The framework uses the Page Object Model design pattern where:
- Each web page is represented by a class
- Page elements are defined as class attributes using locator tuples
- Page interactions are implemented as class methods
- Test logic is separated from page implementation

Example:
```python
class LoginPage:
    username = (By.ID, "username")
    password = (By.ID, "password")
    
    def login(self, user, pwd):
        self.driver.find_element(*self.username).send_keys(user)
        self.driver.find_element(*self.password).send_keys(pwd)
```

## Configuration

The `conftest.py` file contains PyTest fixtures and configuration:
- **browser fixture**: Initializes and manages the WebDriver instance
- Automatically handles browser setup and teardown
- Maximizes browser window for test execution

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**B Sandeep**

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Future Enhancements

- Add support for multiple browsers (Firefox, Edge, Safari)
- Implement parallel test execution
- Add API testing capabilities
- Integrate with CI/CD pipelines
- Add screenshot capture on test failures
- Implement data-driven testing with external data sources
- Add logging functionality
