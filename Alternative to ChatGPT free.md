write an article to apply to # Artificial Corner publication
all requirements in https://artificialcorner.com/write-for-artificial-corner-85c3cbcfda0?gi=5cbb5a870788

it mast be in Draft first
do it tomorrow 17-04


check on notes 2023-04-16
#freeGPT refer to 
[[2023-04-16]] ora.sh (obsidian://open?vault=medium%20articles&file=2023-04-16)



[[2023-04-16]] poe  # 1
[[2023-04-16]] GhjostTogether to check what people do with chatgpt



# How to train ChatGPT on your own text (Chat with your own data, train a text AI to generate content about your docs, book, website, etc)
https://mythicalai.substack.com/p/how-to-train-chatgpt-on-your-own

But luckily for us, there are four techniques we can use today, to get text generator models to use our own text and information.

The three methods are:

1.  Give the AI the data in the prompt
    
2.  Fine-tune a GPT3 model
    
3.  Use a paid service
    
4.  Use an embedding database to feed the needed data into the prompt

# 1. Give the AI the data in the prompt

The easiest way to have the AI answer interact with your data is to give it the data needed in the prompt.

You can just hand GPT3 a chunk of text and then ask it to interact with it. This works relatively well.

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F1d6a837f-48d2-42da-8cf2-566687ec2cf2_1560x1180.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F1d6a837f-48d2-42da-8cf2-566687ec2cf2_1560x1180.png)

The issue with this method is there is a limit to the amount of text you can give to GPT3.

The limit is there because running AI models is computationally expensive. If you handed GPT3 1,000 pages of text in the prompt, GPT3 would need to go through each word to understand what it is, what it means, and its relationship to other words.

OpenAI has set the prompt input limit at 4,000 tokens or approximately ~3,000 words. What is a token? [From this site by OpenAI](https://platform.openai.com/tokenizer):

> The GPT family of models process text using **tokens, which are common sequences of characters found in text**. The models understand the statistical relationships between these tokens, and excel at producing the next token in a sequence of tokens.
> 
> You can use the tool below to understand how a piece of text would be tokenized by the API, and the total count of tokens in that piece of text.

If you try to submit something that is too long you will get this error:

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F432afee1-a502-4d3e-9431-762c5da15ece_1622x322.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F432afee1-a502-4d3e-9431-762c5da15ece_1622x322.png)

A helpful rule of thumb is that one token generally corresponds to ~4 characters of text for common English text. This translates to one token for roughly ¾ of a word, so 100 tokens ≈ 75 words. If you are not sure how much you can submit, paste it into the little tool on the OpenAI website and it will tell you how many tokens your text is.

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4793be4d-8f46-4882-b5df-a5884742e241_1484x1044.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4793be4d-8f46-4882-b5df-a5884742e241_1484x1044.png)

But what if you want to have the AI use more than 3,000 words?

We need to step up our game. We need to fine-tune GPT3.

# 2. Fine-tune GPT3 using your own text

Fine-tuning is where you take an existing model, and then add in your own data on top. We take OpenAI’s base model GPT3, and train a new model on a curated dataset that we supply.

This is great because we don’t have to feed billions of words and buy hundreds of GPUs to train our own model from scratch. We just teach GPT3 about our text.

Even better, OpenAI has an official API that lets you do this. All you need is a to run one command pointing at your text, and it will fine-tune you a GPT3 model which you can then use in the playground or via the API.

Unfortunately, it is not as easy (yet) as handing GPT3 all your text.  
  
You have to give it text in a structured format, essentially telling it how it should try to generate text, based on your data and inputs.

You need to create bunch of examples of what the prompt would be, and then what the answer would be. It would look something like this.

`{"prompt": "<prompt text>", "completion": "<ideal generated text>"}   {"prompt": "<prompt text>", "completion": "<ideal generated text>"}   {"prompt": "<prompt text>", "completion": "<ideal generated text>"}`

After you have all these [prompt - generated text] examples, you package them up in a folder and submit them to the OpenAI API.

This requires some knowledge of programming (ChatGPT can help you figure this out as well) but [this article walks you through it](https://harishgarg.com/writing/how-to-fine-tune-gpt-3-api/).

A neat trick, is you can also give some of your text to ChatGPT and ask it to create the prompt completion for you.

For example I handed ChatGPT the entire article about [creating consistent characters in Stable Diffusion](https://mythicalai.substack.com/p/how-to-create-consistent-characters) from last week, and asked it to create question and answered from it.

[

![](https://substackcdn.com/image/fetch/w_56,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2ec85cdd-a5fe-4d40-b0cd-a77efcb94d38_536x536.png)Mythical AI

How to create consistent characters in Stable Diffusion

Hello, Josh from Mythical AI here. My baby boy just got two bottom teeth, and it is surprising how hard he can bite 🦷👶🏼. Let’s jump into this week’s AI deep dive! Generative AI art has a problem with character consistency. You can make awesome images, but the images are going to be different each time, due to the nature of diffusion models, …

Read more

2 months ago · Josh Dance

](https://mythicalai.substack.com/p/how-to-create-consistent-characters?utm_source=substack&utm_campaign=post_embed&utm_medium=web)

It did a pretty good job.

[

![](https://substackcdn.com/image/fetch/w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4971d9d4-25d8-4839-8a09-27b29b4b8dd0_1600x700.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4971d9d4-25d8-4839-8a09-27b29b4b8dd0_1600x700.png)

I would need to fix, define, and correct a lot of the output, but it is a good starting point.

Once your model is done being fine tuned, you can test it out in the [OpenAI playground](https://platform.openai.com/playground) by selecting the model drop down, and picking the model you created and named.

[

![](https://substackcdn.com/image/fetch/w_424,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdb678a1b-8fb7-4197-a7be-9fe1a9865a14_1174x882.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fdb678a1b-8fb7-4197-a7be-9fe1a9865a14_1174x882.png)

### How much does it cost to fine-tune GPT3 using your own text? 💵

Because processing all of your text costs money, they charge you for this, but they give you a discount. Fine-tuning a model is charged at 50% of the cost of running the model.

The most powerful and expensive GPT3 model, Davinci, costs $0.0200 or 2 cents per / 1000 tokens.

The entire Harry Potter series has 1,084,170 words. So fine-tuning Davinci on just the words in the entire series, one time would cost about 1,084,170 words *.75 = 813,127.5 tokens / 1000 = 813.1 thousand token bundles * 0.02 cents = $16.26

**Update March 2023 -** OpenAI cut the price by 10x.

[

![Twitter avatar for @DrJimFan](https://substackcdn.com/image/twitter_name/w_96/DrJimFan.jpg)

Jim Fan @DrJimFan

It only costs $4.3 (!!) to process the ENTIRE Harry Potter series, combined, with ChatGPT’s new pricing. That’s less than a cup of ☕️ in SF! Economy of scale really casts spells and changes everything, doesn’t it? Calculation: all 7 Harry Potter books add up to 1.08 million… https://t.co/i5aD2VjARX

![Image](https://substackcdn.com/image/fetch/w_600,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fpbs.substack.com%2Fmedia%2FFqOdvxXaYAA8p7i.jpg)



](https://twitter.com/DrJimFan/status/1631320939836370952)[

3:49 PM ∙ Mar 2, 2023

---

1,551Likes211Retweets



](https://twitter.com/DrJimFan/status/1631320939836370952)

However, the default number your tokens are used to train (called an epoch) is 4. So multiple your number of training tokens by 4 to get a more accurate price.

To get good results, you would not be able to just send the text. You would need to create prompts, and then the ideal generated text pairs. So this would inflate the number of

If all of this seems difficult, you are correct. That is why a bunch of companies have sprouted up that automate this. This leads us to our next method of training GPT on your own text.

# 3. Use a paid service

There are a number of services that let you give them text content, which they will then use to generate a GPT-powered chatbot for you.

I haven’t used any of these services but they all seem like they would work.

**[https://www.filechat.io/](https://www.filechat.io/)** - Upload your PDF and start asking questions to your personalized chatbot.

**[https://www.chatbase.co/](https://www.chatbase.co/)** - Upload a PDF and ask a GPT-based chatbot to answer questions on it.

**[https://www.docuchat.io/](https://www.docuchat.io/)** - You upload documents. They feed your content to your chatbot.

**[https://www.humata.ai/](https://www.humata.ai/)** - Created an AI research assistant where you can ask questions about any file (i.e. technical paper, report, etc) in English and automatically get the answer. Humata is like ChatGPT for your files.

**[https://www.customgpt.ai/](https://www.customgpt.ai/)** - Ingests your website and creates a chatbot from the content.

[https://www.chatpdf.com/](https://www.chatpdf.com/)

[chattypdf.com/](http://chattypdf.com/)

[https://myaskai.com/](https://myaskai.com/)

[https://godly.ai/](https://godly.ai/)

[http://humata.ai](http://humata.ai/)

[https://beta.tunify.ai/](https://beta.tunify.ai/)

[https://www.usefini.com/](https://www.usefini.com/)

[https://askyourpdf.com/](https://askyourpdf.com/)

[https://ingestai.io/](https://ingestai.io/)

Since they are not open source we don’t know exactly what each service is doing, but odds are, they are using the last method, which is ‘use an embedding database to feed the needed data into the prompt’. This is the most difficult method of training a chatbot on your own data but scales the best. Let’s dig into it.


# 4. Use an embedding database to feed the needed data into the prompt

If you don’t know what embeddings are, please [read this section of the article](https://mythicalai.substack.com/i/89476982/what-are-embeddings-in-machine-learning) and then come back.

Fine-tuning GPT can be super effective if you have a defined use case. But if you are not sure what users will be asking for, it can be effective to put all your content into an embedding database and then pull out related data and put that into the prompt.

For example, let’s say you wrote a book about places to eat in New York. You could take that content and put it into an embedding database.

Just like latitude and longitude can help you tell how close two cities are on a map, embeddings do the same kind of thing for text chunks. If you want to know if two pieces of text are similar, you just calculate the embeddings for them and compare them. Text chunks with embeddings that are “closer” together are similar.

This would store chunks of your book in a map of space, putting chunks that are more related for example phrases about pizza and phrases about Italian food, closer together and phrases that are less related, for example, phrases about pizza and phrases about soup, further apart.

Next, you accept the user input and embed it as well. This is super useful because then you know how similar the phrase is to your content.

If someone typed in a prompt that mentions spaghetti, they might not have mentioned ‘Italian food’ specifically. But since you have your content and the user phrase embedded, you can see how similar they are. ‘Italian food’ and ‘spaghetti’ will probably be close so you can take the sections of your book that talk about Italian food, put them into the prompt, then return the output to the user.

Here is an example of how that could work.

The user asks ‘What is the best spaghetti in New York?’  
  
You take the phrase `What is the best spaghetti in New York?` and embed it with your content.

A passage you wrote about `Fiaschetteria Pistoia: Petite Tuscan is one of the best Italian restaurant Fiaschetteria Pistoia makes up for its size with charm — the servers are brusque yet friendly, and everything they make is a celebration of the genre.` related very closely to the user’s question. You know this because they are placed close together in the embedding database. This is important because Fiaschetteria Pistoia has great spaghetti but your text didn’t mention it directly. But because we know how close they those two chunks of text are, we can use that info.

So you take the user prompt and your content about Fiaschetteria Pistoia which has great spaghetti but the text and put them into a prompt that you would then send to GPT.

This will help GPT know your content and it can be very flexible.

Dan Shipper has a great article where he explains exactly how he did this with a Substack newsletter here.

[

![](https://substackcdn.com/image/fetch/w_56,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F40b73d36-7447-4f52-83b5-4bbf44b9324a_1200x1200.png)Lenny's Newsletter

I built a Lenny chatbot using GPT-3. Here’s how to build your own.

👋 Hey, Lenny here! Welcome to this month’s ✨ free edition ✨ of Lenny’s Newsletter. Each week I humbly tackle reader questions about building product, driving growth, and working with humans. If you’re not a subscriber, here’s what you missed this month…

Read more

2 months ago · 159 likes · 36 comments · Dan Shipper

](https://www.lennysnewsletter.com/p/i-built-a-lenny-chatbot-using-gpt?utm_source=substack&utm_campaign=post_embed&utm_medium=web)

While more complicated you can use embeddings to stuff prompts and this can drastically improve the results you are getting.  
  
You can of course use embeddings along with a fine-tuned GPT3 model for hopefully even more accuracy and value.

**Update Feb 2023 -** this is why open source is cool. Someone made a library that will do this basically for you. The tweet is inaccurate, it is embedding then feeding relevant info into the prompt, but it is still easier to do now.

[

![Twitter avatar for @IroncladDev](https://substackcdn.com/image/twitter_name/w_96/IroncladDev.jpg)

IroncladDev 🚀 @IroncladDev

How to train a chatbot on your company's documentation with @LangChainAI in ten minutes 🧵👇

](https://twitter.com/IroncladDev/status/1629534148091162626)[

5:29 PM ∙ Feb 25, 2023

---

580Likes87Retweets



](https://twitter.com/IroncladDev/status/1629534148091162626)

Update March 2023 - It gets even easier. PDF to Ask my Book site in 60 seconds.

[https://www.steamship.com/build/ask-my-book-site](https://www.steamship.com/build/ask-my-book-site)

# Scenarios or use cases for training GPT3 on your own data

We covered 4 different methods to train GPT3 on your own text. Here are some interesting use cases.

### Personalized email generator

Prepare a dataset from the emails you have sent, and then fine-tune a DaVinci model on this dataset. You now will have a personalized email generator to follow your style and write emails for you.

### A chatbot that talks in the style of someone famous

Chat with a famous author, like Isaac Asimov or Carl Sagan. Prepare a dataset of their books or words and then fine-tune GPT3.

### Blog posts

Write blog posts in your style, with your information.

### Chat with an author or a book

Sahil wrote a book and [made a site where you could ask that book questions](https://www.youtube.com/watch?v=V3RTA9ZbEPw).

### Customer Service

Train GPT3 on your help docs and style so customers can get quick answers.

What did I miss? Are any other methods or use cases you find compelling? Let me know in the comments.  
  
See you next week!

-Josh



## Llama.cpp for your local LangChain
As far as I know, LangChain might be what you're looking for if you're interacting with a custom, local LLM. It supports llama.cpp, which is the backend for the alpaca-electron you have. [https://python.langchain.com/en/latest/ecosystem/llamacpp.html](https://python.langchain.com/en/latest/ecosystem/llamacpp.html)

contribution by
[

![Guodong (Troy) Zhao](https://miro.medium.com/v2/resize:fill:176:176/1*KCPjHtbAW4sbuelpRphnog.png)



](https://medium.com/@guodong_zhao?source=---two_column_layout_sidebar----------------------------------)

[

## Guodong (Troy) Zhao

](https://medium.com/@guodong_zhao?source=---two_column_layout_sidebar----------------------------------)

[2.1K Followers](https://medium.com/@guodong_zhao/followers?source=---two_column_layout_sidebar----------------------------------)

💻 Product Manager | AI | HealthTech | EdTech | CMU HCII Alum | Curious Learner | [https://www.linkedin.com/in/guodongzhao/](https://www.linkedin.com/in/guodongzhao/)



# LLM on your documents
https://youtu.be/TLf90ipMzfE
# ChatGPT for YOUR OWN PDF files with LangChain

[![](https://yt3.ggpht.com/qGZcIHs93S6ydl_7QpU1uHtO_i8nOKyPCk5j7_zEXTpQ5SyY45WsBNfJks0JwV03WsroHG0x=s88-c-k-c0x00ffffff-no-rj)](https://www.youtube.com/@engineerprompt)

[Prompt Engineering](https://www.youtube.com/@engineerprompt)

73.2K subscribers

Subscribe

2.1K

Share

Download

79,263 views Premiered Apr 4, 2023 [#LangChain](https://www.youtube.com/hashtag/langchain) [#StepbyStep](https://www.youtube.com/hashtag/stepbystep) [#NLP](https://www.youtube.com/hashtag/nlp)

If you're looking to harness the power of large language models for your data, this is the video for you. In this tutorial, you'll discover how to utilize LangChain to extract valuable information from your PDFs, utilizing OpenAI Text Embeddings. Step-by-step, we'll guide you through setting up LangChain to communicate with your PDF files, enabling you to conduct efficient and effective information retrieval. By the end of this video, you'll have the skills you need to leverage advanced language processing technology and elevate your data analysis. Links: Google Colab Notebook: [https://colab.research.google.com/dri...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbWxIRUMtXzZVSFlfS3A2REF6bmEtSDJ3Y2dNd3xBQ3Jtc0tsOGdhNk13UkM2Y3pDU1EyT0hmNU1sV1NtY0EzNnNfcy1YdlF4VnUxYmVYZjJEaGNGVmhzSnl1VTNXVEd0d0FDNGEzWGhWS1ljUUxJTC1PX2cyVzg0YmctcFpPQjZTNHd2VkFBc2VkZUlGaERHN2tNcw&q=https%3A%2F%2Fcolab.research.google.com%2Fdrive%2F181BSOH6KF_1o2lFG8DQ6eJd2MZyiSBNt%3Fusp%3Dsharing&v=TLf90ipMzfE) LangChain Documentation: [https://python.langchain.com/en/lates...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbFdWbUtXRElVVmVzbmU1a1ExeUViZzdYV3hzZ3xBQ3Jtc0tuWUU3Uzc2N1QzNEhVVlJKVV9uZWszNF9nZlp1M2RTTGZjbzVXQ2NEVFR6cDlnZnBEMDRyZUVDOVIwNmQzZ2tFWkZ5MkE2NGlSN2d2MmNkQzBxNlM2bzM4RmdldW40akx5RlNmQkJ3NE5yNFQtY1JJMA&q=https%3A%2F%2Fpython.langchain.com%2Fen%2Flatest%2Findex.html&v=TLf90ipMzfE) OpenAI API: [https://platform.openai.com/account/b...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbUY1QzVIRm13U1RrZHE1dHBFN2xpSjNLR3lOQXxBQ3Jtc0ttc3BfX0NaTjYxeDJOQ21jN1ZuQTdQeklIZ1J3Y3FYelFUTDNoUmV6Rm5rSnZ2VU84MHJZeTZyQ0pyRDBtUWVKQlhFMUJSdmdVVTFkSzd1TjlOem14VkpjTzJmSTdLWGFwdDgyT3RIS2hLRnpMWnp6TQ&q=https%3A%2F%2Fplatform.openai.com%2Faccount%2Fbilling%2Foverview&v=TLf90ipMzfE) GPT4All Technical Report: [https://s3.amazonaws.com/static.nomic...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbDJid1JJY0Q1UDVyUW9OYm1PTkJRRlp0S3F4Z3xBQ3Jtc0ttTmpBWEdEUEdNbEg2TkRLb2t0NHhPekJwRUk5RjdwUXotNm0xY1RiemUybG1RLWZwWEh4dmJOTVVzR1MyUzNuNXRVeXo4SEM4Z0U5MUw3YW1Ia1ZyQUtyaVlzekJBYVltb2ZIWUNkVXBWMzU4UDRkTQ&q=https%3A%2F%2Fs3.amazonaws.com%2Fstatic.nomic.ai%2Fgpt4all%2F2023_GPT4All_Technical_Report.pdf&v=TLf90ipMzfE) ☕ Buy me a Coffee: [https://ko-fi.com/promptengineering](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbk9mNS1oQzd6S09BQmtVelc4Umd3MHlvNUFCd3xBQ3Jtc0trUEhNXzVKZXVITzFoNXJBZndqNW03cDBqVVhIWTNWSEItR2VKaHlvdzZXN2lJQzdLMDZuZlltcDZmWEM1YU00alBHRllST1Z1aW1iRzBadkJLSFlTVHJIcXVxdy1idHhuQkRyYTNuMVBWS2xfaUxPYw&q=https%3A%2F%2Fko-fi.com%2Fpromptengineering&v=TLf90ipMzfE)


https://www.youtube.com/watch?v=E-CNrXhSvLg
# Query Your Own Notes With LangChain

[![](https://yt3.ggpht.com/MNpTvJYLrzNiQAm0LCtv2ugLu785eMnBzDe38bqqe7h73kEE4b0HGVdwIurq1jO3W4htzrvRDA=s88-c-k-c0x00ffffff-no-rj)](https://www.youtube.com/@automatalearninglab)

[Automata Learning Lab](https://www.youtube.com/@automatalearninglab)

940 subscribers

Subscribe

38

Share

Download

693 views Apr 10, 2023 [Automations](https://www.youtube.com/playlist?list=PLXViheZpea0Q8bNxs3ind1UbcBuh3Osq7)

In this video, I demonstrate how to use LangChain to ask questions and gain insights from your notes using natural language. We'll be using Obsidian as our note-taking app and integrating LangChain to elevate our productivity and understanding of our own notes and thoughts. [00:00](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=0s) - Introduction [00:15](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=15s) - Loading Obsidian Loader & Setting Up path to the notes folder [00:41](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=41s) - Creating Vector Store Index with ChromaDB [01:31](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=91s) - Querying Notes with LangChain [01:40](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=100s) - Example 1: Asking Specific Questions [03:30](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=210s) - Example 2: Asking for Insight [05:10](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=310s) - Example 3: Asking for Retrieval [06:30](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=390s) - Reflecting on LangChain Capabilities [07:48](https://www.youtube.com/watch?v=E-CNrXhSvLg&t=468s) - Conclusion




