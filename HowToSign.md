# Introduction #
Enzyme API is web based API set to utilize different types of documents. It requires signing for every HTTP request. In order to get signed request to Enzyme API, you first need to register your API at the Enzyme API Center, which helps using and managing Enzyme API for developers. If you've done register your API at the Center, then you're ready to use Enzyme API.

# Signing Enzyme API #
You can see the API Key and the Signature Key at the API Info page. Two trailing key values are most important thing in signing stage. API Key is used to identifying API request in public. It is always exposed in your final request URL. On the contrary, Signature Key is used to Identifying API request in private. It is never exposed in public, nor should be. If your Signature Key was exposed to anonymous, it means your API identity was stolen. So keep it undisclosed in safe place.

We provide libraries, called enzyme-sign, for helping signing API request by language. Currently, there are two language support: java, php. You can find one which you prefer on our source repository.

# Request Parameter #
Request for Enzyme API is represented as a form of URI. So you can say that it consists of Host, Path and Parameter(Name/Value Pair) set. Host and Path are static value you can easily set: http://member.thinkfree.com and /enzyme/api/. Parameters related with signing stage are:

  * apikey: API Key
  * ts: Current UTC timestamp with timezone. e.g. 2009123112595900
  * nonce: Just random bits.
  * sigalg: Algorithm used in signing. For now 'hmacsha1'.
  * sig: Signature. Varies in every request.

# Signing API Request Using enzyme-sign Library #
enzyme-sign library provides a way of generating properly signed request. As a result to calling, you will get partial string to be used in requesting. If you append this string to Host and Path, and assemble with other parameters related with document to utilize, then you're ready to send that request to Enzyme immediately. Check Enzyme API Reference page for putting into other parameters.