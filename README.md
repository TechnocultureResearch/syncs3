
# syncs3

To give a document sync experience(and eficciency) like 'repo sync', or 'awscli s3 sync', and so forth. Permit records to be transferred on downloaded **ONLY** on the off chance that there is a distinction in the document's local cs remote duplicate. 
Give this as a convinience bundle for involving distant resources in journals.  




## Acknowledgements

 - [JSchulte01](https://gist.github.com/JSchulte01/9ba3f56cb53e2fb447445d9ba6537912)
## Tech Stack

**Language:** Python 3.8.2

## Developing syncs3
To install syncs3, along with the tools ypu need to develop and run tests, run the following in ypur virtualenv:

```bash
$ pip install -e .[dev]
```

## Usage/Examples

### Example 1: Upload object on aws
```python
'''Create object of the LocalObjectCache to initialize the bucket name and prefix.'''
bucket_name = bucket_name
prefix = prefix_name
obj = syncs3(bucket_name, prefix)

'''uploading a obj.'''
__filename__ = file_name
key = os.path.abspath(__filename__)
obj.upload_obj(key)
```

### Example 2: Download object from aws
```python
'''Downloading a key from obj.'''  
__filename__ = file_name
key = os.path.join(obj.prefix, __filename__)

''' download_obj takes a parameter tag which is the value of tag which is returned when the object is uploaded on the aws.'''
obj.download_obj(key, tag_value)

```

### Example 3: sync data of remote s3 bucket and local 
```python
"""Syncs the data of remote s3 bucket and local directory."""
obj.sync()

```

### Example 4: Delete all files form local cache
```python
"""Delete all files from the local cache."""
obj.close()

```
### Example 5: Pickle and un-pickle the self object between multiprocessing pools

```python
"""It takes an argument bucket_name. If bucket name is given then it will change the bucket name else returns the current bucket name and set it at none."""
obj.set_bucket()

```
### Example 6: Calculate s3 e-tag of a file
```python
filename__ = file_name
key = os.path.abspath(filename__)
'''open file on `rb` mode '''
file = open(key, 'rb') 
'''returns a tag of the file '''
obj.calculate_s3_etag(file)
```

### Example 7: Get local file storage path of a given file key
```python
filename__ = file_name
key = os.path.abspath(filename__)
'''Returns a local file storage path for a given file key '''
obj.get_path(key)
```