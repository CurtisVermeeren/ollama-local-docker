# Local Ollama using Docker
Docker compose is setup to use Nvidia GPUs. Ollama runs on port `11434` and models are mounted locally in the `ollama` directory.

Create the docker container `docker compose up`. 

Start the docker container `docker compose start`

Stop the container `docker compose stop` 

Remove the container `docker compose down`

## Ollama Models
A selection of Ollama models can be found in the [Ollama Library](https://ollama.com/library)

List all models `ollama list` 

Pull a model `ollama pull llama3.1`

## Ollama Rest API

### Generate a response
```
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.1",
  "prompt":"Why is the sky blue?",
  "stream": false
}'
```
In this example the llama3.1 model is used. stream set to false will return a single response object rather than a stream of objects.

### Generate a chat completion
```
curl http://localhost:11434/api/chat -d '{
  "model": "llama3.1",
  "messages": [
    {
      "role": "user",
      "content": "why is the sky blue?"
    }
  ],
  "stream": false
}'
```
To add history using the API you would need to append the response message from the assistant then the next user question. 