# How to create Vue Components that don't break

Too many times, I find a component to use to only find out that it does not work. At least not until you spend an hour or so figuring out how the component was made. I believe that there are a few standards that all component creators should follow and should increase the likeliness of the components working. 

## Distribution builds

Please stop publising the SRC. This should be saved for development and not published on NPM. People consuming your component do not care about what your dev dependencies are and will most likely conflict with theirs. 

For example, you may use Stylus for your css processor but I use Sass on mine. In this situation, your component will break when I import your Stylus based component.

From here, I can either decide to install the stylus loader to try and address the problem but most likely I will move on to the next componet that promises something similar. 

## Server Side Rendering

This one is a tricky one and really not your fault if you created a component that broke when running from the server. Normally, the issue lies from the library that you are writing a component wrapper for. Meaning, the library expects window to be available and defined - which is not when running within node. 

There is no one size fit all solution here but if you use `require` instead of `import` to load the library in, then you have the flexibility to initiliaze the lirbrary from Vue's `mounted` hook. 

I know this doesn't look pretty but unless you have the clout to get the library owners to modularize, this is probably easiest way to accomplish this. 



I thought I would have more examples, but at a high level, I think releasing Distribution builds and thinking of Server Side Rendering handles all the cases of componets not working for me. I would love to hear from others of other examples! I really want to spread the word and improve Vue's component ecosystem. 



