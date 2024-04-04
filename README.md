# Telegraph
[![PyPI](https://img.shields.io/pypi/v/telegraph.svg)](https://pypi.python.org/pypi/telegraph)
![Python Versions](https://img.shields.io/pypi/pyversions/telegraph.svg)
![License](https://img.shields.io/github/license/python273/telegraph.svg)

#### Python Telegraph API wrapper

- [Documentation](https://python-telegraph.readthedocs.io/en/latest/)

```bash
python3 -m pip install telegraph
```
# Usage

#### It is recommended to use `Telegraph` as a context manager. By doing this, you can make sure that connections are correctly cleaned up when leaving the `with` block. However, you also have the option to use `.close()` to explicitly close the connection.

### Sync Example
 As context manager
 ```python
 from telegraph import Telegraph

def main():
    with Telegraph() as telegraph:
        telegraph.create_account(short_name='Telegraph')
        response = telegraph.create_page(
            'Telegraph Python',
            html_content='<p>Hello, world!</p>'
        )
        print(response['url'])
main()
 ```
 As .close()

```python
from telegraph import Telegraph

def main():
    telegraph = Telegraph()
    try:
        telegraph.create_account(short_name='Telegraph')
        response = telegraph.create_page(
            'Telegraph Python',
            html_content='<p>Hello, world!</p>'
        )
        print(response['url'])
    except Exception:
        ...
    finally:
        telegraph.close()
main()

```

### Async Example
 As context manager
 ```python
import asyncio
from telegraph import AsyncTelegraph

async def main():
    async with AsyncTelegraph() as telegraph:
        await telegraph.create_account(short_name='Telegraph')
        response = await telegraph.create_page(
            'Telegraph Python',
            html_content='<p>Hello, world!</p>'
        )
        print(response['url'])
asyncio.run(main())
 ```
 As .close()

```python
import asyncio
from telegraph import AsyncTelegraph

async def main():
    telegraph = AsyncTelegraph()
    try:
        await telegraph.create_account(short_name='Telegraph')
        response = await telegraph.create_page(
            'Telegraph Python',
            html_content='<p>Hello, world!</p>'
        )
        print(response['url'])
    except Exception:
        ...
    finally:
        await telegraph.close()
asyncio.run(main())
```


#### Use `UploadFile` (Synchronous), `AsyncUploadFile` (Asynchronous) for upload files to Telegraph server.
> This is not part of official API, Use at own risk. &
> Allowed only .jpg, .jpeg, .png, .gif and .mp4 files.

### Sync Example
```python
from telegraph import UploadFile

def main():
    urls = UploadFile(['ex1.jpg', 'ex2.jpeg', 'ex3.png', 'ex4.gif', 'ex5.mp4'])
    for url in urls: print(url)
main()
```

### Async Example
```python
import asyncio
from telegraph import AsyncUploadFile

async def main():
    urls = await AsyncUploadFile(['ex1.jpg', 'ex2.jpeg', 'ex3.png', 'ex4.gif', 'ex5.mp4'])
    for url in urls: print(url)
asyncio.run(main())
```

# Credits
#### With ❤️ Made By @python273
#### Version 3.0.0 implemented by @Sasivarnasarma
#### Thanks To All Our Contributors
<a href="https://github.com/python273/telegraph/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=python273/telegraph" />
</a>
