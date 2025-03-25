# Things to consider before writing tests

- What I am testing - is standalone or does it have any dependencies.
- Unit tests are for standalone code.

```python
# Simple class (post.py)
class Post:
    def __init__(self, title, content):
        self.title = title
        self.content = content
        
    def json(self):
        return {
            'title': self.title,
            'content': self.content,
        }

# Test to go with it, this will make sure if I make any changes to Post class if that breaks code, I would be able to catch it in the test

# Simple test using unittest
# tests/post_test.py
from unittest import TestCase
from post import Post

class PostTest(TestCase):
    def test_create_post(self):
        p = Post('Test', 'Test Content')
        self.assertEqual('Test', p.title)
        self.assertEqual('Test Content', p.content)

    # Testing Dictionaries
    def test_json(self):
        p = Post('Test', 'Test Content')
        expected = {'title': 'Test', 'content': 'Test Content'}
        self.assertDictEqual(expected, p.json())
```