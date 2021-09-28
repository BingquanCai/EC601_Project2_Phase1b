# EC601_Project2_Phase1b

- 2021 Fall Boston University Class EC601 Project 2 Phase 1(b)

- Bingquan Cai

## Google Natural Language Processing (NLP)

The Google Natural Language Processing (NLP) has powerful pre-trained models. They empowers developers to easily apply natural language understanding (NLU) to their applications with features including sentiment analysis, entity analysis, entity sentiment analysis, content classification, and syntax analysis.

## Using Cloud Natural Language API

I will use Google Cloud Shell to write test programs to exercise different Google NLP APIs. Google Cloud Shell is a command running environment that runs in the cloud. This Debian-based virtual machine can load any development tools you need (gcloud, bq, git, etc.) and provides a permanent 5 GB home directory.

We can create API keys and save them in environment variables so that we don't need to insert API key values repeatedly each time we call the API. We can save the key in Cloud Shell and replace <Personal_API_KEY> below with our API keys.

`export API_KEY=<Personal_API_KEY>`

## Constructing requests for analyzing entities in text

Requests made to the Natural Language API can be saved in advance in the request.json file. First, we generate this file in Cloud Shell.

`touch request.json`

Then, use a text editor to open the generated file. Add the following to the file request.json.

request.json

```
{
  "document":{
    "type":"PLAIN_TEXT",
    "content":"Whatever you want to analyze"
  }
}
```

In this request, the value of the `type` attribute can be `PLAIN_TEXT` or `HTML`. The `content` holds the text to be sent to the Natural Language API for analysis. Natural Language API also supports sending files stored in Google Cloud Storage directly. To send a file directly from Google Cloud Storage, replace `content` with `gcsContentUri` and set its value to the uri address of the file in the cloud.

In this program, I want to analyze the sentence 'Boston is the best city I have ever stayed in so far. I love everything about Boston except the long and freezing winters.'

## Sentiment Analysis with Natural Language API

Sends the request to the API's analyzeSentiment endpoint.

`curl "https://language.googleapis.com/v1/documents:analyzeSentiment?key=${API_KEY}" -s -X POST -H "Content-Type: application/json" --data-binary @request.json`

Response

```
{
  "documentSentiment": {
    "magnitude": 1.3,
    "score": 0.6
  },
  "language": "en",
  "sentences": [
    {
      "text": {
        "content": "Boston is the greatest city I have ever stayed in so far.",
        "beginOffset": -1
      },
      "sentiment": {
        "magnitude": 0.9,
        "score": 0.9
      }
    },
    {
      "text": {
        "content": "I love everything about Boston except the long and freezing winters.",
        "beginOffset": -1
      },
      "sentiment": {
        "magnitude": 0.3,
        "score": 0.3
      }
    }
  ]
}
```

A response value to the sentence of 0.6 score indicates a document which is relatively positive in emotion, while the value of 1.3 indicates a slightly emotional document. In particular， the first sentence of the sentence contains a very high positive score of 0.9.
