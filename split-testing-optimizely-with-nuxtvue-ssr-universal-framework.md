I'm attempting to use Optimizely, to perform some a/b testing on my pages. However, using a framework like Nuxt, brings in on a lot of challenges. The main reason is that Optimizely or others like them have a hard time \(maybe not possible\) to properly tackle server side rendered, client hydrated conent. 

Using the web visualizer, optimizely either breaks or has a nasty Flash of Content issue. The reason for this is due to the SSR and the Client hydration life cycle.

1. If the optimizely experiment is activated before client hydration, optimizely will replace the content but the replaced content will be reverted back to the original when the client hydration lifecycle finishes. 

1. If the optimizely experiment is ran after client hydration, due to the server side rendering the original content will be shown the user until client hydration finishes and the experiment is toggled on. Usually 100-300ms depending on the page. 

I've tried tackling this issue from many different angles without real success. I'm hoping that switching over to the FullStack product can address these issues related to SSR Rendering of Universal frameworks but at a road block due to Optimizely's sdk's being broken up into Client side and Server side.

My main objective is to toggle on an experiment in my code - which toggles an experiment state on. Once this state is turned on, both the server and client executes and renders the page using this state.

Few questions here.

1. What does the activate code do and how does it differ from the server and client SDK? Does it make any kind of outbound message to optimizely?

2. Can I use the client SDK from node to get a variant? Is http client used in the SDK universal like \(axios\) ?

3. in terms of approaches, should I activate from both the server and client SDK? Does this cause any issue?

Lot of open questions and generally not sure if what I'm attempting is possible. I would love to hear back and suggestions on how to tackle this cleanly. If anyone has example implementation that would be great!

