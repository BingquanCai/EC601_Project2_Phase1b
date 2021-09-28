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
    "content":"Whatever you want to"
  }
}
```
