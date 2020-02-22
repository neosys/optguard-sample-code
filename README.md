# optguard-sample-code

Some example code in PHP and Javascript (JS) to demonstrate the integration of the optGuard API. 

There are two ways to integrate:

<b>Method 1:</b> Include the PHP code into a PHP website template (RECOMMENDED).
One should choose this method, if their website supports PHP and can include our few lines of PHP code on landing pages to protect.

<b>Method 2:</b> Embed a JS script in every page of the website. The script will proxy for the PHP script by calling it in a JS script tag. 
As an alternative to method 1, a JS script solution will work on static HTML pages. It will "proxy" the PHP script by calling it as the remote target of the JS event (obviously, the configured PHP script must be hosted SOMEWHERE that supports PHP). Note that this is also a good way to protect a network of sites that all share a single, configured PHP file.

Since bots tend <b><i>not</i></b> to run Javascript (JS), one could argue that relying on a JS script solution would miss the majority of the bots. However, the bots <b><i>we</i></b> want to catch must support JS in order to fraudulently click advertisements. So, for our purposes, we can assume that JS is supported by all visitors we care about. 

However, method 2 is the only solution for websites that cannot include our PHP script (such as with static HTML pages or some types of PHP, opCode, or CDN caching). 


<b>PHP Script Purpose:</b> Once executed, our code will pull the visitor's IP via the web server and PHP framework. This simple script will pass along the IP address of the visitor to our API, using the configured access and secret keys. 

**API Details**

This plugin currently uses the following optGuard API endpoint(s).

### `/v1/check`

Check an IP Address.

**HTTP Method:** `GET`

**Endpoint**

```bash
https://api.optguard.com/v1/check
```

**Parameters**

Pass these along as query string parameters on your endpoint.

| Field       | Type   | Description                | Example     | Required |
|-------------|--------|----------------------------|-------------|----------|
| `access_key`| String | Enter your Access Key      | `123456`    | Yes      |
| `secret_key`| String | Enter your Secret Key      | `987`       | Yes      |
| `ip`        | String | IP Address to be checked   | `127.0.0.1` | Yes      |

**Sample API Calls**

```bash
# Check an IP Address (async, non-blocking)
https://api.optguard.com/v1/check?access_key=123456&secret_key=987&ip=127.0.0.1
```

**Sample Response**

The API will return a JSON object with a msg, status_msg, and status.

1. msg: A human-readable message regarding the request.
2. status_msg: A textual representation of the status code.
3. status: A numeric representation of the status of the request (usually 0 or 1).


```json
{
    "msg": "IP is on the Blacklist",
    "status_msg": "IP_SUSPECT",
    "status": 1
}
```
