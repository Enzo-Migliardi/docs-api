---
description: Add job
---

# \[POST\] /job/indexing

This endpoint accepts json files.

Please find below an example of json job that you can upload.

```bash
{
    "name": "Data Engineer",
    "agent_key": "agent_key",
    "reference": "Job's reference abc",
    "url": "https://www.pole-emploi.ai/jobs/data_engineer",
    "summary": "As an engineer for the Data Engineering Infrastructure team,
                you will design, build, scale, and evolve our data engineering
                platform, services and tooling. Your work will have a critical 
                impact on all areas of business: powering core data pipelines,
                supporting detailed internal analytics, calculating customer
                usage, securing our platform, and much more.",
    "location": {
                  "text": "Dampierre en Burly (45)",
                  "geopoint": {
                      "lat": 47.7667,
                      "lon": 2.5167
                  }
                 },
    "sections": [{
                    "name": "profile",
                    "title": "Searched Profile",
                    "description": "Bac+5"
                  },
                  .
                  .
                  .
                  ],
    "skills": [{
                  "name": "python",
                  "value": null
               },
               {
                  "name": "spark",
                  "value": 0.9
               },
               .
               .
               .
               ],
    "languages": [{
                     "name": "english",
                     "value": 1
                  },
                 {  
                     "name": "french",
                     "value": 1
                  },
                  .
                  .
                  .
                  ],
    "tags": [{
                "name": "archive",
                "value": true
             },
             {  
                "name": "tag example",
                "value": "tag"
              },
              .
              .
              .
              ],
    "ranges_date": [{
                       "name": "Dates",
                       "value_min": "2020-05-18T21:59",
                       "value_max": "2020-09-15T21:59"
                    },
                    .
                    .
                    .
                    ],
    "ranges_float": [{
                       "name": "salary",
                       "value_min": 30,
                       "value_max": 40,
                       "unit": "eur"
                    },
                    .
                    .
                    .
                    ],
    "metadatas": [{
                     "name": "metadata example",
                     "value": "metadata"
                  },
                  .
                  .
                  .
                  ],
}
```

You can include complementary information such as :

* job's tags,
* job's metadata.

{% api-method method="post" host="https://api.hrflow.ai/v1" path="/job/indexing" %}
{% api-method-summary %}
Post /job/indexing
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to post job json.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-API-KEY" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="X-USER-EMAIL" type="string" required=true %}
User's email.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="board\_key" type="string" required=true %}
Board key
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
Job's name
{% endapi-method-parameter %}

{% api-method-parameter name="agent\_key" type="string" required=false %}
Agent key
{% endapi-method-parameter %}

{% api-method-parameter name="reference" type="string" required=true %}
Job reference
{% endapi-method-parameter %}

{% api-method-parameter name="created\_at" type="string" required=true %}
Creation date as iso Format
{% endapi-method-parameter %}

{% api-method-parameter name="url" type="string" required=true %}
Job's url
{% endapi-method-parameter %}

{% api-method-parameter name="summary" type="string" required=true %}
Job's summary
{% endapi-method-parameter %}

{% api-method-parameter name="sections" type="array" required=true %}
Job's sections  
\(ie. \[{"name": "section\_name", "title": "section\_title", ""
{% endapi-method-parameter %}

{% api-method-parameter name="location" type="object" required=true %}
Job's location  
\(ie. {  
        "text": "xx rue XXXX" ,  
        "geopoint": {  
                              "lat":38.299637 ,  
                              "lng": -122.657535  
                             }  
        }\)
{% endapi-method-parameter %}

{% api-method-parameter name="skills" type="array" required=true %}
Job's skills  
\(ie. \[{"name": "skill", "type":"hard or soft", "value":0.8}, ...\]\)
{% endapi-method-parameter %}

{% api-method-parameter name="languages" type="array" required=true %}
Job's languages  
\(ie. \[{"name": "language", "value": 0.7}, ...\]\)
{% endapi-method-parameter %}

{% api-method-parameter name="tags" type="array" required=true %}
Job's tags  
\(ie. \[{"name": "tag", "value":"tag\_value"}, ...\]\)
{% endapi-method-parameter %}

{% api-method-parameter name="metadatas" type="array" required=true %}
Job's metadatas   
\(ie. \[{"name": "meta", "value":"meta\_value"}, ...\]\)
{% endapi-method-parameter %}

{% api-method-parameter name="ranges\_float" type="array" required=true %}
Job's ranges float
{% endapi-method-parameter %}

{% api-method-parameter name="ranges\_date" type="array" required=true %}
Job's ranges date
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Job successfully created.
{% endapi-method-response-example-description %}

```scheme
{
    "code": 201,
    "message": "Job created",
    "data": {
        "id": id,
        "key": "job_key",
        "reference": "Job's reference 12",
        "name": "Data Engineer",
        "url": "https://www.pole-emploi.ai/jobs/data_engineer",
        "summary": "As an engineer for the Data Engineering Infrastructure team, you will design, build, scale, and evolve our data engineering platform, services and tooling. Your work will have a critical  impact on all areas of business: powering core data pipelines,  supporting detailed internal analytics, calculating customer  usage, securing our platform, and much more.",
        "sections": [
            {
                "name": "profile",
                "title": "Searched Profile",
                "description": "Bac+5"
            }
        ],
        "location": {
            "text": "Dampierre en Burly (45)",
            "lat": null,
            "lng": null,
            "gmaps": null,
            "fields": null
        },
        "skills": [
            {
                "name": "python",
                "value": null
            },
            {
                "name": "spark",
                "value": 0.90000000000000002
            }
        ],
        "languages": [
            {
                "name": "english",
                "value": 1
            },
            {
                "name": "french",
                "value": 1
            }
        ],
        "tags": [
            {
                "name": "archive",
                "value": true
            },
            {
                "name": "tag example",
                "value": "tag"
            }
        ],
        "ranges_float": [
            {
                "name": "salary",
                "value_min": 30,
                "value_max": 40,
                "unit": "eur"
            }
        ],
        "ranges_date": [
            {
                "name": "Dates",
                "value_min": "2020-05-18T21:59",
                "value_max": "2020-09-15T21:59"
            }
        ],
        "updated_at": "2020-06-11T14:43:29+0000",
        "created_at": "2020-06-11T14:43:29+0000"
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Invalid secret key.
{% endapi-method-response-example-description %}

```bash
{
    "code": 401,
    "message": "Unauthorized. Invalid secret key: xxxxx "
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="Python" %}
```python
import hrflow as hf

client = hf.client(api_secret="Your API Key", api_user="Your API user email")

data = {
    "name": "Data Engineer",
    "agent_key": "agent_key",
    "reference": "Job's reference abc",
    "url": "https://www.pole-emploi.ai/jobs/data_engineer",
    "summary": "As an engineer for the Data Engineering Infrastructure team,
                you will design, build, scale, and evolve our data engineering
                platform, services and tooling. Your work will have a critical 
                impact on all areas of business: powering core data pipelines,
                supporting detailed internal analytics, calculating customer
                usage, securing our platform, and much more.",
    "location": {
                  "text": "Dampierre en Burly (45)",
                  "geopoint": {
                      "lat": 47.7667,
                      "lon": 2.5167
                  }
                 },
    "sections": [{
                    "name": "profile",
                    "title": "Searched Profile",
                    "description": "Bac+5"
                  }],
    "skills": [{
                  "name": "python",None               },
               {
                  "name": "spark",
                  "value": 0.9
               }],
    "languages": [{
                     "name": "english",
                     "value": 1
                  },
                 {  
                     "name": "french",
                     "value": 1
                  }],
    "tags": [{
                "name": "archive",
                "value": True
             },
             {  
                "name": "tag example",
                "value": "tag"
              }],
    "ranges_date": [{
                       "name": "Dates",
                       "value_min": "2020-05-18T21:59",
                       "value_max": "2020-09-15T21:59"
                    }],
    "ranges_float": [{
                       "name": "salary",
                       "value_min": 30,
                       "value_max": 40,
                       "unit": "eur"
                    }],
    "metadatas": [{
                     "name": "metadata example",
                     "value": "metadata"
                  }],
}

client.job.indexing.add_json(board_key="board_key", job_json=data)
```
{% endtab %}

{% tab title="Javascript" %}
```javascript
import Hrflow from 'hrflow';
const client = new Hrflow({ 
    api_secret: "Your API Key",
    api_user: "Your API user email" 
});

client.job.indexing.addJosn("board_key", {
    "name": "Data Engineer",
    "agent_key": "agent_key",
    "reference": "Job's reference abc",
    "url": "https://www.pole-emploi.ai/jobs/data_engineer",
    "summary": "As an engineer for the Data Engineering Infrastructure team,
                you will design, build, scale, and evolve our data engineering
                platform, services and tooling. Your work will have a critical 
                impact on all areas of business: powering core data pipelines,
                supporting detailed internal analytics, calculating customer
                usage, securing our platform, and much more.",
    "location": {
                  "text": "Dampierre en Burly (45)",
                  "geopoint": {
                      "lat": 47.7667,
                      "lon": 2.5167
                  }
                 },
    "sections": [{
                    "name": "profile",
                    "title": "Searched Profile",
                    "description": "Bac+5"
                  }],
    "skills": [{
                  "name": "python",
                  "value": null
               },
               {
                  "name": "spark",
                  "value": 0.9
               }],
    "languages": [{
                     "name": "english",
                     "value": 1
                  },
                 {  
                     "name": "french",
                     "value": 1
                  }],
    "tags": [{
                "name": "archive",
                "value": true
             },
             {  
                "name": "tag example",
                "value": "tag"
              }],
    "ranges_date": [{
                       "name": "Dates",
                       "value_min": "2020-05-18T21:59",
                       "value_max": "2020-09-15T21:59"
                    }],
    "ranges_float": [{
                       "name": "salary",
                       "value_min": 30,
                       "value_max": 40,
                       "unit": "eur"
                    }],
    "metadatas": [{
                     "name": "metadata example",
                     "value": "metadata"
                  }],
});
```
{% endtab %}
{% endtabs %}

