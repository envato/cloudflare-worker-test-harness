# Cloudflare Worker Test Harness

### Usage

- Add it to your `package.json` file.

  ```js
  {
    // ...

    "devDependencies": {
      "cloudflare-worker-test-harness": "git://github.com/envato/cloudflare-worker-test-harness.git#master"
    }

    // ...
  }
  ```

- Run `yarn install`
- Include it in your test

  ```js
  require('cloudflare-worker-test-harness')
  ```

- Write a test that excercises the `fetch` call

  ```js
  const handleRequest = require('./worker')

  test('gets a HTTP 200', async () => {
    fetch.mockResponse(JSON.stringify({status: 200}))
    const request = new Request('http://example.com/', {
      cf: { cacheTtl: 30 }
    })
    expect(request.cf.cacheTtl).toBe(30)
  })
  ```

### What is included?

This repository aims to match the [Cloudflare Worker API
reference][worker_api_reference]. Any variation of this should be
considered a bug.

- [x] [Fetch API][fetch_api_docs] with [`cf` object][cf_feature_docs] for controlling features
- [ ] [ECMAScript Builtins][emcascript_api_docs]
- [ ] [Web Global APIs][web_global_api_docs]
- [ ] [Encoding API][encoding_api_docs]
- [ ] [URL API][url_api_docs]
- [ ] [Streams API][streams_api_docs]
- [ ] [Web Crypto API][web_crypto_api_docs]

### Running tests

```
npm test
```

[worker_api_reference]: https://developers.cloudflare.com/workers/reference/
[fetch_api_docs]: https://developer.mozilla.org/docs/Web/API/Fetch_API
[cf_feature_docs]: https://developers.cloudflare.com/workers/reference/cloudflare-features/
[emcascript_api_docs]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference
[web_global_api_docs]: https://developer.mozilla.org/docs/Web/API/WindowOrWorkerGlobalScope
[encoding_api_docs]: https://developer.mozilla.org/docs/Web/API/Encoding_API
[url_api_docs]: https://developer.mozilla.org/docs/Web/API/URL
[streams_api_docs]: https://developer.mozilla.org/docs/Web/API/Streams_API
[web_crypto_api_docs]: https://developer.mozilla.org/docs/Web/API/Web_Crypto_API
