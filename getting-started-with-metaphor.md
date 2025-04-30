# Getting started with Metaphor

Prompting AIs can be hard.
While they sometimes do exactly what you want, they often get it wrong.
Even when you do get what you want, it's far too easy to lose track of what what worked and why.
It's even harder when you want to work with multiple AIs.

Metaphor is a simple, open-source, prompt creation language that lets you create consistent, reusable prompts that
work across a variety of AI platforms.
It lets you capture the what you need your AI to understand so it has a clear idea what you want it to do, without
needing to guess (hallcinate) any details.

Metaphor is AI agnostic.
It works the same way with large language models from all major AI vendors, including Anthropic, DeepSeek, Google,
Mistral, OpenAI, and xAI, making it easy to switch between them and find the right one for your needs.

The Metaphor language is easy to learn.
It has only a few keywords and takes only a few minutes to get started.
This guide will show you how.

## How is Metaphor used?

Metaphor is designed to be used at the start of a new conversation with an AI large language model (LLM).
It sets the scene for the LLM, ensuring it knows how you want it behave, what you want it to do, and allows you to
tell it everything it needs to know to do that.

You might ask "AIs know almost everything - why do I need to do this?"
The answer is surprisingly simple.
AI models know a huge amount but they have no idea what you're trying achieve or how you want them to help us unless
you tell them.

One way to think about this is if you want to ask another human how to do something, you have to explain these things
to them.
AIs are no different.
Unlike most people, however, LLMs don't remember what you've said to them before.
Fortunately, they are incredibly fast at reading so they can get up to speed in a few seconds if you give
them the full picture from the outset.

While forgetfulness might seem like a nuissance, working with LLMs this way can have surprising benefits.
Here are a few:

- Each new conversation is a fresh start so the LLM doesn't bring misunderstandings or disagreements from
  previous conversations into the new one.
- You can have the same conversation with different LLMs and see what new insights come from each one.
- It's possible to start a conversation with one AI and finish it with a different one.

## A first Metaphor prompt

All Metaphor prompts start with the same structure.
First, there's a "role" that describes the role you want your AI to play.
Second, there's a "context" that tells the AI everything it needs to know that's specific to what you want it to do.
Third (and last), there's an "action" that tells the AI what you want it to do.

Each of these has a special keyword in the Metaphor language, specifically, `Role`, `Context`, and `Action`.
The capital letters at the start of each keyword are important.

Here's an example:

```metaphor
Role:
    You are a world-class python programmer.

Context:
    I need a simple program to demonstrate using the Metaphor language to solve a programming problem.

Action:
    Build me a "hello world" program.
```

If you give this to an AI (perhaps via a web chat interface) you'll probably find it does the right thing without
any extra work, but to use Metaphor properly you need to use a prompt compiler.

## The m6rc prompt compiler

The prompt compiler checks that the Metaphor prompt is structured the right way and allows for more advanced
functionality.  For now, you don't need to worry about other functionality.

What you will need is the right sort of prompt compiler.
This is called `m6rc`, short for "Metaphor compiler".
In case you're wondering, "m6r" is short for Metaphor - it's an "m", 6 letters, and an "r".

There are currently two version of the `m6rc` software.
One is a command line version and you can find this at [https://github.com/m6r-ai/m6rc](https://github.com/m6r-ai/m6rc).
The other is built into a GUI-based application called "Humbug".
If you don't have this already you can find instructions on how to download the latest free (open source) version
from [https://m6r.ai/humbug](https://m6r.ai/humbug).

For this getting started guide you're going to be using Humbug.

## Getting started with Humbug

Humbug is a front end for LLMs, but doesn't contain an LLM.
It supports many popular LLMs from Anthropic, DeepSeek, Google, Mistral, OpenAI, and xAI.
It also supports local installations of Ollama.
With the exception of Ollama, all the others are commercial services that require API (application programming interface)
keys to use them.

Generally commercial LLM providers require you to pay in advance.
The costs can be very low, but both Google and Mistral currently offer a free tier of API access for testing and you
can use them.

You can follow these sign up links:

- Google: [https://ai.google.dev/gemini-api/docs/api-key](https://ai.google.dev/gemini-api/docs/api-key)
- Mistral: [https://docs.mistral.ai/getting-started/quickstart/](https://docs.mistral.ai/getting-started/quickstart/)

Next you can start Humbug.

### First steps

Once it's running for the first time you'll see something a little like this:

![start screen](img/start-screen.webp)

If you go to the "Humbug" menu and select "Preferences" you will see a user settings page:

![API key settings](img/api-keys.webp)

Copy your Google and/or Mistral (or any other) API keys into the appropriate lines and then click OK.

You'll want to check the API keys are working properly.  The easiest way to do this is to start a conversation, but
Humbug needs you to do one thing first.

### Mindspaces

Humbug is designed to let you work on lots of different projects and have different settings and preferences for each.
It does this by using a "Mindspace".
Each project uses a different mindspace.
For this getting started guide the easiest choice is to create a new mindspace using the "New Mindspace" option from
the "File" menu.
You can use an existing folder for your mindspace, but it's probably best to create a new folder when you click
"New Mindspace".

Once you've selected the location for your new mindspace, you'll see a new dialog that looks something like this:

![New Mindspace](img/new-mindspace.webp)

The dialog shows Humbug will always create a "conversations" folder, and defaults to creating a "metaphor" folder.
It has an option to also create a "src" folder for software development if you want it.

### A test conversation

To test your API keys, start a conversation by selecting "New Conversation" from the "File" menu.
Humbug will choose a default AI model and conversations settings for you to use.
You can change these using the "Mindspace Settings" option in "Edit" menu, and you can also change them on a
conversation-by-conversation basis by usign the "Conversation Settings" option.
When you do either of these you will be presented with AI models that are available with your API keys.

You'll see a screen something like this:

![First conversation screen](img/first-conversation.webp)

You can type a message to the AI in the message box at the bottom.
When you're done, you submit the message by pressing Cmd+J on Mac OS, or Ctrl+J on Windows or Linux.
The return/enter key doesn't submit messages because this message box is designed to let you write very complex
messages to the AI and you don't want to accidently submit them when you're trying to lay out text.

If you say something like "Hello", you should see a response back from the AI.
If you get a system error message then re-check your API keys have been entered correctly in the Preferences dialog.

![First conversation screen with a reply from the AI](img/first-conversation-success.webp)

## Using m6rc

The `m6rc` Metaphor compiler works on files you create.
By convention these have a `.m6r` file extension type.

### Metaphor files

You can create and edit Metaphor files using the file editor within Humbug.
To create a new file, use the "New File" option in the "File" menu.

Until you save a file, the editor isn't sure what sort of a file it is and so won't highlight the different parts of
the Metaphor language, but if you use the "Save As" option in the "File" menu you can save your new file as
something like `Hello.m6r`.
An ideal place to save this is in the `metaphor` folder that was created when you created the new mindspace.

To get started, let's go back to the simple Metaphor file from earlier:

```metaphor
Role:
    You are a world-class python programmer.

Context:
    I need a simple program to demonstrate using the Metaphor language to solve a programming problem.

Action:
    Build me a "hello world" program.
```

Copy and paste this into your new `Hello.m6r` file, then save it, and you should see it looks something like this:

![A simple metaphor prompt file](img/hello-m6r.webp)

### Compiling a prompt

There are a couple of different ways to use the Metaphor compiler inside Humbug.
The most powerful one is to use the "System Shell" as that lets you compile and start a Metaphor-based prompt in one
command.
The simpler option, however, is to use the "New Metaphor Conversation" option in the "File" menu.

When the dialog appears, choose your `Hello.m6r` file and click OK.

If all goes well you will see a new conversation tab opened and the output of `m6rc` will be shown in the message box.
This isn't automatically sent to the AI so you can change the AI model and conversation settings if you want to.
Once you're happy with those settings you submit the prompt with Cmd+J (Mac OS) or Ctrl+J (Windows or Linux).

If everything works, the AI will respond with a simple one-line python program - the famous "Hello, world!".
The format may be a little different, as AIs will not respond the same way every time.

![Hello, world output](img/hello-world.webp)

### A slight aside about Humbug

You may have noticed that Humbug has a `conversations` folder.
If you expand this you'll see both of the conversations we've had with the AI are stored there.
You can safely delete these if you no longer want them, but they can be a great record of your conversations with
different LLMs.
You can also give them more meaningful names, as by default they have the date and time of the conversation as their name.

You may also have seen there are icons/buttons on the right hand side of parts of the conversations.
These let you copy or save sections of conversations.
This is really useful when they contain file contents or code fragments you want to use elewhere.
There are also some powerful conversation management features, although they are out of scope for this tutorial.

### Metaphor conversations are just conversations

If you look at your Metaphor conversation you'll see that after the AI responds you can carry on the conversation.
This is just like you would do with an app or web-based chat interface.

For example, you can ask the AI questions about what it has just done:

![Asking about the hello world programm](img/first-question.webp)

This ability to ask questions is incredibly useful.
Here are some benefits:

- You can ask the AI any questions you might have about what you gave it in the Metaphor prompt.
- You can ask the AI explain any part of what it generates.
- You can ask it how confident it is in its answers.
- You can even ask how to improve your prompt if want to be able to use it again in the future.

## More about Metaphor's syntax

Here's the simple example again:

```metaphor
Role:
    You are a world-class python programmer.

Context:
    I need a simple program to demonstrate using the Metaphor language to solve a programming problem.

Action:
    Build me a "hello world" program.
```

There are a few more important parts to this:

- After each keyword is a `:`.
  This is because all Metaphor keywords allow additional information on the keyword line.
- Each block of text is indented by 4 spaces.
  This spacing is important because it lets the Metaphor compiler check the contents of the Metaphor file.

After each of these 3 types of keyword, Metaphor let's you specify a section/subsection heading.
This is like the section headings in a normal document.
These are useful because they let you structure things more clearly.
They are also useful because you can discuss specific parts of the Metaphor prompt with the AI.

## To Do:

- syntax
- iterating to a solution
- getting started from nothing
- interactions with other people are easier.
