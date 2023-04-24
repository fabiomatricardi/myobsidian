https://opensource.com/article/20/12/tqdm-python

However, not all things are predictable. One of the least predictable things is network speed. When you download a big file, the only way to measure progress is to explicitly check how much has been downloaded:

```python
url = "https://www.python.org/ftp/python/3.9.0/Python-3.9.0.tgz"
import httpx
with httpx.stream("GET", url) as response:
    total = int(response.headers["Content-Length"])
    with tqdm.tqdm(total=total) as progress:
        for chunk in response.iter_bytes():
            progress.update(len(chunk))
```

![tqdm output](https://opensource.com/sites/default/files/uploads/output_18_0.png "tqdm output")

(Moshe Zadke, [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/))

