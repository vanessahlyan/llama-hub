# Google Drive Loader

This loader reads files from Google Drive using folder or file ids. To use this loader, you need to pass in a list of file id's or folder id.

### folder_id

You can extract a folder_id directly from its drive URL.

For example, the folder_id of `https://drive.google.com/drive/folders/1w7XryYu6mL9VLmfyqUkA4_fRnDbsCqV-` is `1w7XryYu6mL9VLmfyqUkA4_fRnDbsCqV-`.

### file_id

You can extract a file_id directly from its sharable drive URL.

For example, the file_id of `https://drive.google.com/file/d/1LEqD_zQiOizKrBKZYKJtER_h6i49wE-y/view?usp=sharing` is `1LEqD_zQiOizKrBKZYKJtER_h6i49wE-y`.

## Usage

We need `credentials.json` and `client_secrets.json` files to use this reader.

1. You need to get your `credentials.json` file by following the steps mentioned [here](https://developers.google.com/drive/api/v3/quickstart/python)
2. Create duplicate file of `credentials.json` with name `client_secrets.json` which will be used by pydrive for downloading files.

Finally, make sure you enable "Google Drive API" in the console of your Google App.

```python
from gpt_index import download_loader

GoogleDriveReader = download_loader("GoogleDriveReader")

loader = GoogleDriveReader()

#### Using folder id
documents = loader.load_data(folder_id="folderid")

#### Using file ids
documents = loader.load_data(file_ids=["fileid1", "fileid2"])
```

This loader is designed to be used as a way to load data into [GPT Index](https://github.com/jerryjliu/gpt_index/tree/main/gpt_index) and/or subsequently used as a Tool in a [LangChain](https://github.com/hwchase17/langchain) Agent. See [here](https://github.com/emptycrown/llama-hub/tree/main) for examples.
