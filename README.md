# Cacophony SERVER REST api  python_client V1
Python client for the REST [Cacophony API server](https://github.com/TheCacophonyProject/cacophony-api).



## Installation

This API client requires Python 3.6 or later.

* Create a virtualenv using your preferred method.
* Install dependencies: `pip install -r requirements.txt`
* python setup.py install

## Configuration from a user perspecitve
>### Client Instance setup
>Open an instance of the client and use credentials directly
>``` python
>from cacophonyREST_python_clientV1.cacophonyClient.client import CacophonyClient
>cp_client = CacophonyClient(baseurl=<SERVER-URL>, 
>                            username=<USER-NAME>, 
>                            password=<USER-PASSWORD>)
>```
>or alternatively with credential stored  in `defaultconfig.json`
>```python
>from cacophonyREST_python_clientV1.cacophonyClient.client import CacophonyClient
>from cacophonyREST_python_clientV1.cacophonyClient.config import Config
>
>config=Config().load_config(config_file=os.path.join(
>    os.getcwd(),'defaultconfig.json'))
>
>cp_client = CacophonyClient(config.api_url,
>                            username=config.admin_username ,
>                            password=config.admin_password)
>```
>


## API calls

By default the most recent 100 recordings accessible to the user
account are queried but `API.query()` does support a number of
filtering options. The API server supports arbitrary queries so feel
free to extend `API.query()` if required.


## Configuration from a device perspecitve
# TODO: check device and create tests





## Testing

#TODO: expand testing in both `client_test.py` and `client_test_with_server.py`

Testing uses the pythony unittest framework where by both unit and integration testing is done.

`test\test_client.py` is tests without requiring a server `nose2 --verbosity 2  CacophonyClient.test.test_client`

and `test\test_client_with_server` is full integration testing against a server. This is also part of the travis test `nose2 --verbosity 2 CacophonyClient.test.test_with_server`. 
This integration testing does require a local server setup see [travis.yml](travis.yml)

For individual test `nose2 --verbosity 2  CacophonyClient.test.test_client.mockedCacophonyServer.test_query`



