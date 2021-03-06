![Logo](https://raw.githubusercontent.com/jimmytheleaf/astrologly/master/img/Astrologly.png)


Astrologly is the first AAAS (Astrology as a Service) application.

We're disrupting the divination industry through offering elegant, REST-like APIs on top of deep occult knowledge graphs.

We are dedicated to our craft and practice Taurus-driven development (TDD), a software development process that relies on the Taurus's slowness to anger and sensibility in practical decisions.


## API Usage

**Base Endpoint:**


[https://astrologly.herokuapp.com](https://astrologly.herokuapp.com/)

**API Key:**

Your API key is determined by taking the MD5 hash of the year, month, day, and military time of your birth, encoded in url-safe base64. MD5 is totally secure because it is an irreversible hash. Rate-limiting will be determined by the Quincunx aspect of your API key.

Example:

```python
>>> from hashlib import md5
>>> import base64
>>> hash_digest = md5("198301312245").digest()
>>> base64.urlsafe_b64encode(hash_digest)
'zvOLyxDo5LDmI6jHyLDuog=='
```


## Signs Endpoint

####Get:

**Example Query:**

GET [https://astrologly.herokuapp.com/signs/aries/ ](https://astrologly.herokuapp.com/signs/aries/)

**Example Response:**

```json
{
  "data": {
      "description": "The Ram", 
      "element": "Fire", 
      "end": "April 19", 
      "name": "Aries", 
      "quality": "Cardinal", 
      "start": "March 21"
    }
}
```

####List:

**Example Query:**

GET [https://astrologly.herokuapp.com/signs/ ](https://astrologly.herokuapp.com/signs/)

**Example Response:**

```json
{
  "data": [
    {
      "description": "The Ram", 
      "element": "Fire", 
      "end": "April 19", 
      "name": "Aries", 
      "quality": "Cardinal", 
      "start": "March 21"
    }, 
    {
      "description": "The Bull", 
      "element": "Earth", 
      "end": "May 20", 
      "name": "Taurus", 
      "quality": "Fixed", 
      "start": "April 20"
    }
    ...
  ]
}
```


## Natal Reading  Endpoint

#### Basic

**Format:**

/natal/{year}/{month}/{day}/

**Example Query:**

GET [https://astrologly.herokuapp.com/natal/1983/01/31/ ](https://astrologly.herokuapp.com/natal/1983/01/31/)

**Example Response:**

```json
{
  "data": {
    "signs": {
      "sun": {
        "description": "The Water Bearer", 
        "element": "Air", 
        "end": "February 21", 
        "name": "Aquarius", 
        "quality": "Fixed", 
        "start": "January 21"
      }
    }, 
    "source": {
      "date": {
        "day": 31, 
        "month": 1, 
        "year": 1983
      }, 
      "humanized": "32 years ago", 
      "verbose": "Monday January 31, 1983"
    }
  }
}
```

#### Full

**Format:**

/natal/{year}/{month}/{day}/{hour}/{minute}/

**Example Query:**

GET [https://astrologly.herokuapp.com/natal/1983/01/31/12/45/ ](https://astrologly.herokuapp.com/natal/1983/01/31/12/45/)

**Example Response:**

```json

{
  "data": {
    "signs": {
      "moon": {
        "description": "The Scales", 
        "element": "Air", 
        "end": "October 23", 
        "name": "Libra", 
        "quality": "Cardinal", 
        "start": "September 23"
      }, 
      "rising": {
        "description": "The Twins", 
        "element": "Air", 
        "end": "June 21", 
        "name": "Gemini", 
        "quality": "Mutable", 
        "start": "May 21"
      }, 
      "sun": {
        "description": "The Water Bearer", 
        "element": "Air", 
        "end": "February 21", 
        "name": "Aquarius", 
        "quality": "Fixed", 
        "start": "January 21"
      }
    }, 
    "source": {
      "date": {
        "day": 31, 
        "month": 1, 
        "year": 1983
      }, 
      "humanized": "32 years ago", 
      "verbose": "Monday January 31, 1983"
    }
  }
}
```