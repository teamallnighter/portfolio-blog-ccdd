---
template: blog-post
title: "Full Stack Jamstack: Serverless GraphQL"
slug: /blog/fsjs-serverless-graphql
date: 2020-09-03 15:24
description: "This is a serverless database using graphql. "
featuredImage: /assets/cover-2.png
---
## Project: Netlify Functions Serverless GraphQL API

##### Build: React, Netlify Serverless Functions, CSS, Node.js and REACT

##### Features: Serverless, Netlify Functions, Database, API

##### Deployment: Github and Netlify

#### [Demo](https://netlify-ql-2020.netlify.app/api/v1)

##### [Blog Post](https://blog.chrisconnelly.dev/netlify%20functions/netlify/2020/09/03/netlify-graphql-api.html)

- - -

This is a serverless back end for an API with Graph-QL. This is a quick and easy way to store data on a server and have it accessed in a very secure way.

In this example you can [click here](https://netlify-ql-2020.netlify.app/api/v1) and betaken to the Graph-QL playground. Right now there is no login or as this is all dummy data. once you see the play ground you query the api like so:

```json
{
  getUsers{
    gender
    email
    cell
    phone
    nat
    gender
    name{
      first
      last
    }
    location{
      city
      state
      postcode
    }
  }
}
```

You will receive data back that looks like this

```json
"data": {
    "getUsers": \[
      {
        "gender": "male",
        "email": "mhmdmhdy.rdyy@example.com",
        "cell": "0971-221-5758",
        "phone": "050-02060510",
        "nat": "IR",
        "name": {
          "first": "محمدمهدی",
          "last": "رضایی"
        },
        "location": {
          "city": "بابل",
          "state": "فارس",
          "postcode": "84482"
        }
      },
      {
        "gender": "male",
        "email": "bobby.mcdonalid@example.com",
        "cell": "0704-013-114",
        "phone": "015242 51667",
        "nat": "GB",
        "name": {
          "first": "Bobby",
          "last": "Mcdonalid"
        },
        "location": {
          "city": "Sunderland",
          "state": "Greater Manchester",
          "postcode": "PJ1 4UR"
        }
      },
      {
        "gender": "female",
        "email": "yasemin.hurenkamp@example.com",
        "cell": "(469)-311-9413",
        "phone": "(143)-373-3959",
        "nat": "NL",
        "name": {
          "first": "Yasemin",
          "last": "Hurenkamp"
        },
        "location": {
          "city": "Beek en Donk",
          "state": "Zuid-Holland",
          "postcode": "78896"
        }
      },
      {
        "gender": "female",
        "email": "teresa.lee@example.com",
        "cell": "0788-779-010",
        "phone": "01543 80815",
        "nat": "GB",
        "name": {
          "first": "Teresa",
          "last": "Lee"
        },
        "location": {
          "city": "Birmingham",
          "state": "County Tyrone",
          "postcode": "IP3 1UJ"
        }
      },
      {
        "gender": "female",
        "email": "mrl.sdr@example.com",
        "cell": "0974-380-2906",
        "phone": "092-24481530",
        "nat": "IR",
        "name": {
          "first": "مارال",
          "last": "صدر"
        },
        "location": {
          "city": "کاشان",
          "state": "چهارمحال و بختیاری",
          "postcode": "27387"
        }
      },
      {
        "gender": "male",
        "email": "leo.macdonald@example.com",
        "cell": "091-670-3266",
        "phone": "341-961-2793",
        "nat": "CA",
        "name": {
          "first": "Leo",
          "last": "Macdonald"
        },
        "location": {
          "city": "Enterprise",
          "state": "Nova Scotia",
          "postcode": "X9V 6D3"
        }
      },
      {
        "gender": "female",
        "email": "grace.lord@example.com",
        "cell": "081-836-9219",
        "phone": "021-354-5125",
        "nat": "IE",
        "name": {
          "first": "Grace",
          "last": "Lord"
        },
        "location": {
          "city": "Wicklow",
          "state": "Clare",
          "postcode": "42079"
        }
      },
      {
        "gender": "male",
        "email": "reginald.caldwell@example.com",
        "cell": "(706)-341-8875",
        "phone": "(081)-682-0661",
        "nat": "US",
        "name": {
          "first": "Reginald",
          "last": "Caldwell"
        },
        "location": {
          "city": "Riverside",
          "state": "Utah",
          "postcode": "51770"
        }
      },
      {
        "gender": "female",
        "email": "ellie.cunningham@example.com",
        "cell": "081-120-9014",
        "phone": "041-511-3256",
        "nat": "IE",
        "name": {
          "first": "Ellie",
          "last": "Cunningham"
        },
        "location": {
          "city": "Ardee",
          "state": "Louth",
          "postcode": "38595"
        }
      },
      {
        "gender": "male",
        "email": "xavier.leclerc@example.com",
        "cell": "079 184 93 07",
        "phone": "078 963 00 93",
        "nat": "CH",
        "name": {
          "first": "Xavier",
          "last": "Leclerc"
        },
        "location": {
          "city": "Besenbüren",
          "state": "Neuchâtel",
          "postcode": "6806"
        }
      }
    ]
  }
}
```
