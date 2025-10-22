# Automation Testing Practice Project

A comprehensive test automation practice project built with **Cypress** and **Playwright** frameworks, designed to practice UI and API testing against the [Expand Testing Practice Website](https://practice.expandtesting.com/).

## 📋 Table of Contents

- [About the Project](#about-the-project)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Project Structure](#project-structure)
- [Design Patterns & Conventions](#design-patterns--conventions)
  - [Page Object Model (POM)](#page-object-model-pom)
  - [Test Data Management](#test-data-management)
  - [Naming Conventions](#naming-conventions)
  - [Locator Strategy](#locator-strategy)
- [Best Practices](#best-practices)
  - [Test Organization](#test-organization)
  - [Wait Strategies](#wait-strategies)
  - [Assertions](#assertions)
  - [Error Handling](#error-handling)
- [Running Tests](#running-tests)
  - [Cypress](#cypress)
  - [Playwright](#playwright)
- [API Testing](#api-testing)
- [CI/CD Integration](#cicd-integration)
- [Reporting](#reporting)
- [Contributing](#contributing)

---

## About the Project

This project serves as a learning platform for test automation engineers to practice and enhance their skills using modern testing frameworks. The practice website offers various testing scenarios including:

- **UI Testing**: Forms, dynamic elements, authentication, tables, modals, tooltips
- **API Testing**: RESTful endpoints with Swagger documentation
- **Challenging Scenarios**: AJAX calls, async operations, flaky tests, cookie handling
- **Real-world Examples**: E-commerce flows, file uploads, context menus, drag & drop

## Tech Stack

### Frameworks
- **Playwright** (TypeScript) - Modern, reliable end-to-end testing
- **Cypress** (JavaScript/TypeScript) - Fast, easy, and reliable testing for browser-based applications

### Supporting Tools
- **TypeScript** - Type-safe test development
- **ESLint** - Code quality and consistency
- **Prettier** - Code formatting
- **Husky** - Git hooks for quality gates
- **Allure/Mochawesome** - Test reporting
- **GitHub Actions** - CI/CD pipeline

---

## Getting Started

### Prerequisites

Ensure you have the following installed:
- **Node.js** (v18 or higher)
- **npm** or **yarn** or **pnpm**
- **Git**

### Installation

```bash
# Clone the repository
git clone <repository-url>
cd automation-testing-practice

# Install dependencies
npm install

# Install Playwright browsers
npx playwright install

# Verify installation
npm run test:playwright -- --version
npm run test:cypress -- --version
```

---

## Project Structure

```
automation-testing-practice/
├── cypress/
│   ├── e2e/
│   │   ├── ui/
│   │   │   ├── login.cy.ts
│   │   │   ├── forms.cy.ts
│   │   │   └── dynamic-elements.cy.ts
│   │   └── api/
│   │       ├── status-codes.cy.ts
│   │       └── rest-api.cy.ts
│   ├── fixtures/
│   │   ├── users.json
│   │   └── test-data.json
│   ├── support/
│   │   ├── commands.ts
│   │   ├── page-objects/
│   │   │   ├── LoginPage.ts
│   │   │   ├── HomePage.ts
│   │   │   └── BasePage.ts
│   │   └── helpers/
│   │       ├── api-helper.ts
│   │       └── data-generator.ts
│   └── cypress.config.ts
├── playwright/
│   ├── tests/
│   │   ├── ui/
│   │   │   ├── login.spec.ts
│   │   │   ├── forms.spec.ts
│   │   │   └── dynamic-elements.spec.ts
│   │   └── api/
│   │       ├── status-codes.spec.ts
│   │       └── rest-api.spec.ts
│   ├── fixtures/
│   │   ├── users.json
│   │   └── test-data.json
│   ├── page-objects/
│   │   ├── LoginPage.ts
│   │   ├── HomePage.ts
│   │   └── BasePage.ts
│   ├── utils/
│   │   ├── api-helper.ts
│   │   ├── data-generator.ts
│   │   └── test-helpers.ts
│   └── playwright.config.ts
├── .github/
│   └── workflows/
│       ├── cypress.yml
│       └── playwright.yml
├── .eslintrc.js
├── .prettierrc
├── tsconfig.json
└── package.json
```

---

## Design Patterns & Conventions

### Page Object Model (POM)

The **Page Object Model** is the primary design pattern used in this project to improve test maintainability and reduce code duplication.

#### Structure

```typescript
// BasePage.ts - Common functionality
export abstract class BasePage {
  constructor(protected page: Page) {}

  async navigate(url: string): Promise<void> {
    await this.page.goto(url);
  }

  async getTitle(): Promise<string> {
    return await this.page.title();
  }

  async waitForPageLoad(): Promise<void> {
    await this.page.waitForLoadState('domcontentloaded');
  }
}

// LoginPage.ts - Page-specific implementation
export class LoginPage extends BasePage {
  // Locators
  private readonly usernameInput = this.page.locator('#username');
  private readonly passwordInput = this.page.locator('#password');
  private readonly loginButton = this.page.locator('button[type="submit"]');
  private readonly errorMessage = this.page.locator('.alert-danger');

  // Actions
  async login(username: string, password: string): Promise<void> {
    await this.usernameInput.fill(username);
    await this.passwordInput.fill(password);
    await this.loginButton.click();
  }

  async getErrorMessage(): Promise<string> {
    return await this.errorMessage.textContent() || '';
  }

  // Validations
  async isLoginButtonVisible(): Promise<boolean> {
    return await this.loginButton.isVisible();
  }
}
```

#### Key Principles:
- **Single Responsibility**: Each page object represents one page/component
- **Encapsulation**: Locators are private; only actions are exposed
- **Reusability**: Common functionality in BasePage
- **Maintainability**: Changes to UI require updates in one place only

### Test Data Management

#### Fixtures for Static Data

```typescript
// fixtures/users.json
{
  "validUser": {
    "username": "testuser",
    "password": "TestPass123!"
  },
  "invalidUser": {
    "username": "invalid",
    "password": "wrong"
  }
}
```

#### Data Builders for Dynamic Data

```typescript
// utils/data-generator.ts
export class UserDataBuilder {
  private user: User = {
    username: '',
    email: '',
    password: ''
  };

  withRandomUsername(): this {
    this.user.username = `user_${Date.now()}`;
    return this;
  }

  withEmail(email: string): this {
    this.user.email = email;
    return this;
  }

  withPassword(password: string): this {
    this.user.password = password;
    return this;
  }

  build(): User {
    return this.user;
  }
}

// Usage
const user = new UserDataBuilder()
  .withRandomUsername()
  .withEmail('test@example.com')
  .withPassword('SecurePass123!')
  .build();
```

### Naming Conventions

#### Test Files
- **Format**: `feature-name.spec.ts` (Playwright) or `feature-name.cy.ts` (Cypress)
- **Examples**: `login.spec.ts`, `checkout-flow.cy.ts`, `api-authentication.spec.ts`

#### Test Cases
```typescript
// Descriptive, follows Given-When-Then pattern
describe('Login Functionality', () => {
  describe('Valid Credentials', () => {
    it('should successfully log in with valid username and password', async () => {
      // Test implementation
    });
  });

  describe('Invalid Credentials', () => {
    it('should display error message when password is incorrect', async () => {
      // Test implementation
    });

    it('should display error message when username does not exist', async () => {
      // Test implementation
    });
  });
});
```

#### Page Objects & Methods
- **Classes**: PascalCase - `LoginPage`, `ShoppingCartPage`
- **Methods**: camelCase, verb-based - `clickLoginButton()`, `enterUsername()`
- **Locators**: camelCase with descriptive names - `submitButton`, `errorMessageText`

#### Variables
- **Constants**: UPPER_SNAKE_CASE - `BASE_URL`, `DEFAULT_TIMEOUT`
- **Local variables**: camelCase - `username`, `expectedTitle`

### Locator Strategy

Priority order for selecting elements (most to least preferred):

1. **Accessible locators** (ARIA, labels, text):
   ```typescript
   page.getByRole('button', { name: 'Submit' })
   page.getByLabel('Username')
   page.getByText('Welcome back')
   ```

2. **Test IDs** (custom data attributes):
   ```typescript
   page.locator('[data-testid="login-button"]')
   ```

3. **CSS Selectors** (when above aren't available):
   ```typescript
   page.locator('#username')
   page.locator('.error-message')
   ```

4. **XPath** (only as last resort):
   ```typescript
   page.locator('//button[contains(text(), "Submit")]')
   ```

**Best Practices:**
- Avoid brittle selectors (overly specific CSS, text-based when text changes frequently)
- Use multiple fallback locators when necessary
- Avoid index-based selection
- Prefer user-facing attributes over implementation details

---

## Best Practices

### Test Organization

#### Independent Tests
```typescript
// ❌ Bad - Tests depend on each other
test('create user', async () => { /* creates user */ });
test('login with created user', async () => { /* depends on previous test */ });

// ✅ Good - Each test is independent
test('should create a new user', async ({ page }) => {
  // Test has its own setup
});

test('should login with valid credentials', async ({ page }) => {
  // Test has its own setup
});
```

#### Test Hooks
```typescript
describe('Shopping Cart', () => {
  beforeEach(async ({ page }) => {
    // Setup: Navigate and login
    await page.goto('/login');
    await loginPage.login(testUser.username, testUser.password);
  });

  afterEach(async ({ page }) => {
    // Cleanup: Clear cart, logout
    await page.context().clearCookies();
  });

  it('should add item to cart', async ({ page }) => {
    // Test implementation
  });
});
```

### Wait Strategies

#### Playwright Auto-Waiting
Playwright automatically waits for elements - no explicit waits needed in most cases:
```typescript
// Playwright automatically waits for element to be actionable
await page.locator('#submit-button').click();
await page.locator('#username').fill('testuser');
```

#### Explicit Waits (when needed)
```typescript
// Wait for specific condition
await page.waitForSelector('.success-message', { state: 'visible' });
await page.waitForLoadState('networkidle');
await page.waitForResponse(response => 
  response.url().includes('/api/user') && response.status() === 200
);
```

#### Cypress Automatic Retrying
```typescript
// Cypress automatically retries assertions
cy.get('.loading').should('not.exist');
cy.get('.success-message').should('be.visible');

// Explicit wait when needed
cy.wait('@apiRequest');
cy.intercept('GET', '/api/users').as('apiRequest');
```

### Assertions

#### Prefer Soft Assertions for Multiple Checks
```typescript
// Playwright
await expect.soft(page.locator('.title')).toHaveText('Dashboard');
await expect.soft(page.locator('.username')).toContainText('John');
await expect.soft(page.locator('.balance')).toBeVisible();
```

#### Meaningful Error Messages
```typescript
// ❌ Generic assertion
await expect(isVisible).toBeTruthy();

// ✅ Descriptive assertion
await expect(loginButton, 'Login button should be visible on page load')
  .toBeVisible();
```

### Error Handling

#### Try-Catch for Expected Failures
```typescript
test('should handle network failure gracefully', async ({ page }) => {
  await page.route('**/api/users', route => route.abort());
  
  try {
    await page.goto('/users');
    await expect(page.locator('.error-message')).toBeVisible();
  } catch (error) {
    throw new Error(`Expected error message not displayed: ${error}`);
  }
});
```

#### Screenshot on Failure (built-in)
```typescript
// playwright.config.ts
export default defineConfig({
  use: {
    screenshot: 'only-on-failure',
    video: 'retain-on-failure',
    trace: 'on-first-retry',
  },
});
```

---

## Running Tests

### Cypress

```bash
# Open Cypress Test Runner (interactive)
npm run cypress:open

# Run all tests (headless)
npm run cypress:run

# Run specific spec file
npm run cypress:run -- --spec "cypress/e2e/ui/login.cy.ts"

# Run with specific browser
npm run cypress:run -- --browser chrome

# Run tests by tag
npm run cypress:run -- --env grepTags="@smoke"
```

### Playwright

```bash
# Run all tests (headless)
npm run playwright:test

# Run in UI mode (interactive)
npm run playwright:test -- --ui

# Run specific test file
npm run playwright:test tests/ui/login.spec.ts

# Run tests in specific browser
npm run playwright:test -- --project=chromium

# Run tests with specific tag
npm run playwright:test -- --grep @smoke

# Debug mode
npm run playwright:test -- --debug

# Generate test report
npm run playwright:report
```

---

## API Testing

### Playwright API Testing
```typescript
import { test, expect } from '@playwright/test';

test.describe('API Tests - Status Codes', () => {
  test('GET request should return 200', async ({ request }) => {
    const response = await request.get('https://practice.expandtesting.com/status-codes/200');
    expect(response.status()).toBe(200);
  });

  test('POST request with authentication', async ({ request }) => {
    const response = await request.post('https://practice.expandtesting.com/api/auth/login', {
      data: {
        username: 'testuser',
        password: 'testpass'
      }
    });
    
    expect(response.status()).toBe(200);
    const body = await response.json();
    expect(body).toHaveProperty('token');
  });
});
```

### Cypress API Testing
```typescript
describe('API Tests - Status Codes', () => {
  it('GET request should return 200', () => {
    cy.request('GET', 'https://practice.expandtesting.com/status-codes/200')
      .its('status')
      .should('equal', 200);
  });

  it('POST request with authentication', () => {
    cy.request({
      method: 'POST',
      url: 'https://practice.expandtesting.com/api/auth/login',
      body: {
        username: 'testuser',
        password: 'testpass'
      }
    }).then((response) => {
      expect(response.status).to.eq(200);
      expect(response.body).to.have.property('token');
    });
  });
});
```

---

## CI/CD Integration

### GitHub Actions - Playwright

```yaml
# .github/workflows/playwright.yml
name: Playwright Tests

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  test:
    timeout-minutes: 60
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - uses: actions/setup-node@v3
      with:
        node-version: 18
        
    - name: Install dependencies
      run: npm ci
      
    - name: Install Playwright Browsers
      run: npx playwright install --with-deps
      
    - name: Run Playwright tests
      run: npm run playwright:test
      
    - uses: actions/upload-artifact@v3
      if: always()
      with:
        name: playwright-report
        path: playwright-report/
        retention-days: 30
```

### GitHub Actions - Cypress

```yaml
# .github/workflows/cypress.yml
name: Cypress Tests

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  cypress-run:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v3
      
    - name: Cypress run
      uses: cypress-io/github-action@v5
      with:
        build: npm run build
        start: npm start
        wait-on: 'http://localhost:3000'
        
    - uses: actions/upload-artifact@v3
      if: always()
      with:
        name: cypress-screenshots
        path: cypress/screenshots
        
    - uses: actions/upload-artifact@v3
      if: always()
      with:
        name: cypress-videos
        path: cypress/videos
```

---

## Reporting

### Playwright HTML Reporter
Built-in HTML reporter with screenshots and traces:
```bash
npm run playwright:test
npm run playwright:report
```

### Allure Reporter
```bash
# Install Allure
npm install -D @playwright/test allure-playwright
npm install -D allure-commandline

# Run tests with Allure
npm run playwright:test
npx allure generate allure-results --clean
npx allure open allure-report
```

### Cypress Mochawesome Reporter
```bash
# Already configured in cypress.config.ts
npm run cypress:run

# Report generated in: cypress/reports/
```

---

## Contributing

### Code Quality Standards

1. **Linting**: All code must pass ESLint checks
   ```bash
   npm run lint
   npm run lint:fix
   ```

2. **Formatting**: Use Prettier for consistent formatting
   ```bash
   npm run format
   npm run format:check
   ```

3. **Type Safety**: TypeScript strict mode is enabled
   ```bash
   npm run type-check
   ```

### Pull Request Guidelines

1. Create a feature branch from `develop`
2. Write tests following the project conventions
3. Ensure all tests pass locally
4. Update documentation if needed
5. Create PR with clear description
6. Ensure CI/CD pipeline passes

### Commit Message Convention

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add login page object for Playwright
fix: correct selector for submit button
test: add API tests for user endpoints
docs: update README with new examples
refactor: improve data builder pattern
```

---

## Additional Resources

### Recommended Tools & Libraries

- **Faker.js**: Generate realistic test data
- **Dotenv**: Environment variable management
- **Winston/Pino**: Structured logging
- **axe-core**: Accessibility testing
- **Percy/Applitools**: Visual regression testing

### Learning Resources

- [Playwright Documentation](https://playwright.dev/)
- [Cypress Documentation](https://www.cypress.io/)
- [Expand Testing Practice Site](https://practice.expandtesting.com/)
- [Test Automation University](https://testautomationu.applitools.com/)
- [Ministry of Testing](https://www.ministryoftesting.com/)

### Design Patterns to Explore

- **Builder Pattern**: For complex test data creation
- **Factory Pattern**: For creating page objects
- **Strategy Pattern**: For different authentication methods
- **Singleton Pattern**: For configuration management
- **Chain of Responsibility**: For validation flows

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## Support

For questions or issues:
- Open an issue in the repository
- Check existing documentation
- Review practice site documentation at [Expand Testing](https://practice.expandtesting.com/)

---

**Happy Testing! 🚀**
