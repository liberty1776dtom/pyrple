# pyrple
### Python wrapper to make simple *GET* requests with the <a href="http://purple.ai/">Purple Wifi</a> API.

*Purple Wifi* is an enterprise SAAS platform for managing public wifi access across large commercial estates such as property developments, stadiums, or public transportation. The Purple platform comes with a RESTFUL API that can be used to retrieve data about the wifi venues and visitors who have connected to the public wifi.

*Pyrple* is a simple Python wrapper around the Purple API to allow really simple requests to get visitor, venue, and other data out of the platform.

## Installation

*Pyrple* is available for download via pypi:

<code>pip install -U pyrple</code>

## Usage

First create an API instance using public and private keys.

For example, loading credentials from a dictionary:
```json
keys = {"public_key": "abcdefghij123454KLMnoP123",
        "private_key": "qrstuv98765434WxyZ"}
```
we can then create the API instance with:

```python
my_purple = purple(public_key = keys["public_key"], private_key = keys["private_key"])
```

Data can now be retrieved using the built-in methods:

```python
my_purple.venues()
```
returns a simple *json* dictionary of all Purple wifi venues with their unique IDs.


```python
my_purple.venues_json()
```
returns a *json* dictionary of Purple Wifi venues with full details.


```python
my_purple.visitor_json(venue = "12345")
```
returns a *json* dictionary of all visitor info for the specified venue ID. By default it will produce all visitors currently connected at the venue, but optional parameters of <code>date_from</code> and <code>date_to</code> can be supplied in format <code>YYYYMMDD</code> to report on historic data from the given date range.

## Example

In:
```python
my_purple.venues()
```
Out:
```python
{u'Venue 1 - entrance': 52133,
 u'Venue 2 - podium': 44663,
 u'Basement 1': 11223,
 u'Basement 2': 22336,
 u'Residents 1': 51234}
```
