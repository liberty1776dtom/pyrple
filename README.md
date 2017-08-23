# pyrple
### Python wrapper to make simple *GET* requests with the <a href="http://purple.ai/">Purple Wifi</a> API.

*Purple Wifi* is an enterprise SAAS platform for managing public wifi access across large commercial estates such as property developments, stadiums, or public transportation. The Purple platform comes with a RESTFUL API that can be used to retrieve data about the wifi venues and visitors who have connected to the public wifi.

*Pyrple* is a simple Python wrapper around the Purple API to allow really simple requests to get visitor and venue data out of the platform.

## Installation

*Pyrple* is now available for download via pypi:

<code>pip install pyrple</code>

## Usage

You first create an instance using your unique Purple wifi public and private keys.
For example, credentials can be loaded from a locally stored *json* file in format:

```json
{"public_key": "abcdefghij123454KLMnoP123", "private_key": "qrstuv98765434WxyZ"}
```

The API instance can then be created with:

```python
my_purple = purple(public_key = public_key, private_key = private_key)
```

Now retrieve your data using the built in methods:

```python
my_purple.venues()
```
returns a simple *json* dictionary of all your Purple wifi venues with their unique IDs.


```python
my_purple.venues_json()
```
returns a *json* dictionary of your Purple Wifi venues with full details.


```python
my_purple.visitor_json(venue='12345')
```
returns a *json* dictionary of all visitor info for the specified venue ID. By default it will produce all visitors currently connected at the venue, but optional parameters of date_from and date_to can be supplied in format YYYYMMDD to report on historic data from the specified date range.

## Example

```python
my_purple.venues()
```
out:
```python
{u'Venue 1 - entrance': 52133,
 u'Venue 2 - podium': 44663,
 u'Basement 1': 11223,
 u'Basement 2': 22336,
 u'Residents 1': 51234}
```
