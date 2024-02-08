# 🏠 Fully Client-Side Chat Over Documents

Yes, it's another chat over documents implementation... but this one is entirely local!

![](/public/images/demo.gif)

It's a Next.js app that read the content of an uploaded PDF, chunks it, adds it to a vector store, and
performs RAG, all client side. You can even turn off your WiFi after the site loads!

You can see a live version at https://completely-local-pdf-chatbot-llm-powered.vercel.app.

Users will need to download and set up [Ollama](https://ollama.ai), then run the following commands to
allow the site access to a locally running Mistral instance:

```bash
$ OLLAMA_ORIGINS=https://completely-local-pdf-chatbot-llm-powered.vercel.app OLLAMA_HOST=127.0.0.1:11435 ollama serve
```
Then, in another terminal window:

```bash
$ OLLAMA_HOST=127.0.0.1:11435 ollama pull mistral
```

## ⚡ Stack

It uses the following:

- [Voy](https://github.com/tantaraio/voy) as the vector store, fully WASM in the browser.
- [Ollama](https://ollama.ai/) to run an LLM locally and expose it to the web app.
- [LangChain.js](https://js.langchain.com) to call the models, perform retrieval, and generally orchestrate all the pieces.
- [Transformers.js](https://huggingface.co/docs/transformers.js/index) to run open source [Nomic](https://www.nomic.ai/) embeddings in the browser.
  - For more speed on some machines, switch to `"Xenova/all-MiniLM-L6-v2"` in `app/worker.ts`.

I wanted to run as much of the app as possible directly in the browser, but you can swap in [Ollama embeddings](https://js.langchain.com/docs/modules/data_connection/text_embedding/integrations/ollama) as well.

## 🔱 Forking

To run/deploy this yourself, simply fork this repo and install the required dependencies with `yarn`.

There are no required environment variables!
