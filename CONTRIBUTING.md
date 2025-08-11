# Contributing to Steganography Project

Thank you for your interest in contributing to our steganography project! We welcome contributions from developers of all experience levels. This document provides guidelines and information about how to contribute effectively.

## 🤝 How to Contribute

### Types of Contributions We Welcome

- 🐛 **Bug Reports**: Help us identify and fix issues
- 💡 **Feature Requests**: Suggest new functionality or improvements
- 📝 **Documentation**: Improve README, code comments, or add tutorials
- 🔧 **Code Contributions**: Bug fixes, new features, performance improvements
- 🧪 **Testing**: Add unit tests, integration tests, or manual testing
- 🎨 **UI/UX**: Improve user interface and experience
- 🌐 **Translations**: Help make the project accessible to more users

## 🚀 Getting Started

### 1. Fork and Clone the Repository

```bash
# Fork the repository on GitHub, then clone your fork
git clone https://github.com/YOUR_USERNAME/Steganography.git
cd Steganography

# Add the original repository as upstream
git remote add upstream https://github.com/Debanga-06/Steganography.git
```

### 2. Set Up Your Development Environment

```bash
# Create a virtual environment (recommended)
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Install development dependencies
pip install pytest black flake8 mypy
```

### 3. Create a Feature Branch

```bash
# Create and switch to a new branch
git checkout -b feature/your-feature-name

# Or for bug fixes
git checkout -b fix/bug-description
```

## 📋 Development Guidelines

### Code Style and Standards

We follow Python PEP 8 guidelines with some specific conventions:

#### Code Formatting
```bash
# Format code with Black (line length: 88 characters)
black .

# Check code style with flake8
flake8 .

# Type checking with mypy
mypy encrypt_stegano.py
```

#### Naming Conventions
- **Variables**: `snake_case`
- **Functions**: `snake_case`
- **Classes**: `PascalCase`
- **Constants**: `UPPER_SNAKE_CASE`
- **Files**: `snake_case.py`

#### Documentation Standards
```python
def encrypt_message(text: str, key: str) -> bytes:
    """
    Encrypt a text message using AES encryption.
    
    Args:
        text (str): The plaintext message to encrypt
        key (str): The encryption key (must be 32 characters)
        
    Returns:
        bytes: The encrypted message as bytes
        
    Raises:
        ValueError: If key length is invalid
        EncryptionError: If encryption fails
        
    Example:
        >>> encrypted = encrypt_message("Hello World", "my32characterlongencryptionkey!")
        >>> isinstance(encrypted, bytes)
        True
    """
```

### Testing Requirements

#### Writing Tests
- All new features must include unit tests
- Aim for >80% code coverage
- Use descriptive test names
- Test both success and failure scenarios

```python
# Example test structure
import pytest
from encrypt_stegano import encrypt_message, decrypt_message

class TestEncryption:
    def test_encrypt_message_success(self):
        """Test successful message encryption."""
        text = "Test message"
        key = "a" * 32  # 32-character key
        encrypted = encrypt_message(text, key)
        assert isinstance(encrypted, bytes)
        assert len(encrypted) > 0
    
    def test_encrypt_message_invalid_key(self):
        """Test encryption with invalid key length."""
        with pytest.raises(ValueError):
            encrypt_message("Test", "short_key")
```

#### Running Tests
```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=encrypt_stegano

# Run specific test file
pytest tests/test_encryption.py

# Run with verbose output
pytest -v
```

### Git Workflow

#### Commit Message Format
We use conventional commit messages:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```bash
git commit -m "feat: add support for TIFF image format"
git commit -m "fix: handle empty message input gracefully"
git commit -m "docs: update installation instructions"
git commit -m "test: add unit tests for XOR encoding function"
```

#### Branch Management
```bash
# Keep your branch up to date
git fetch upstream
git rebase upstream/main

# Push your changes
git push origin feature/your-feature-name
```

## 🐛 Reporting Issues

### Bug Reports

When reporting bugs, please include:

1. **Clear title** describing the issue
2. **Environment details**: OS, Python version, dependency versions
3. **Steps to reproduce** the issue
4. **Expected behavior**
5. **Actual behavior**
6. **Screenshots** (if applicable)
7. **Error messages** (full traceback)

**Bug Report Template:**
```markdown
**Bug Description**
A clear description of what the bug is.

**Environment**
- OS: [e.g., Windows 10, macOS 12.1, Ubuntu 20.04]
- Python Version: [e.g., 3.9.7]
- Project Version: [e.g., v1.0.0]

**Steps to Reproduce**
1. Go to '...'
2. Click on '...'
3. Run command '...'
4. See error

**Expected Behavior**
What you expected to happen.

**Actual Behavior**
What actually happened.

**Additional Context**
Any other relevant information.
```

### Feature Requests

For feature requests, please provide:

1. **Use case**: Why is this feature needed?
2. **Proposed solution**: How should it work?
3. **Alternatives considered**: Other approaches you've thought about
4. **Additional context**: Screenshots, mockups, examples

## 🔄 Pull Request Process

### Before Submitting

- [ ] Code follows our style guidelines
- [ ] All tests pass (`pytest`)
- [ ] Code is properly documented
- [ ] Commit messages follow our format
- [ ] Branch is up to date with main
- [ ] No merge conflicts

### Submitting Your Pull Request

1. **Create the Pull Request**
   - Use a descriptive title
   - Reference related issues (`Fixes #123`)
   - Provide detailed description

2. **Pull Request Template**
```markdown
## Description
Brief description of changes made.

## Type of Change
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that causes existing functionality to not work as expected)
- [ ] Documentation update

## Testing
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Code is documented
- [ ] Tests added for new functionality
- [ ] Documentation updated if needed

## Related Issues
Fixes #(issue number)
```

### Review Process

1. **Automated Checks**: CI/CD pipeline runs tests and style checks
2. **Code Review**: Maintainers review code for quality and adherence to guidelines
3. **Feedback**: Address any requested changes
4. **Approval**: Once approved, PR will be merged

## 🏗️ Development Setup (Advanced)

### IDE Configuration

#### VS Code Settings
```json
{
    "python.formatting.provider": "black",
    "python.linting.enabled": true,
    "python.linting.flake8Enabled": true,
    "python.linting.mypyEnabled": true,
    "python.testing.pytestEnabled": true
}
```

### Pre-commit Hooks
```bash
# Install pre-commit
pip install pre-commit

# Install hooks
pre-commit install

# Run on all files
pre-commit run --all-files
```

### Docker Development Environment
```dockerfile
FROM python:3.9-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .
CMD ["python", "encrypt_stegano.py"]
```

## 📞 Communication and Support

### Getting Help

- **GitHub Discussions**: For general questions and community discussion
- **Issues**: For bug reports and feature requests
- **Email**: [maintainer-email] for sensitive or urgent matters

### Community Guidelines

- Be respectful and inclusive
- Help others learn and grow
- Provide constructive feedback
- Follow our Code of Conduct

## 🎯 Priority Areas

We're particularly interested in contributions in these areas:

1. **Performance Optimization**: Improve processing speed for large images
2. **Additional File Formats**: Support for more image and data types
3. **Security Enhancements**: Advanced encryption methods and steganalysis resistance
4. **User Interface**: GUI development with modern frameworks
5. **Documentation**: Tutorials, examples, and API documentation
6. **Testing**: Comprehensive test coverage and edge case handling

## 🏆 Recognition

Contributors will be recognized in:
- README.md contributors section
- Release notes for significant contributions
- Special mentions for outstanding contributions

## 📜 License

By contributing to this project, you agree that your contributions will be licensed under the same MIT License that covers the project. See the [LICENSE](LICENSE) file for details.

---

Thank you for contributing to the Steganography project! Your efforts help make secure communication more accessible to everyone. 🚀
