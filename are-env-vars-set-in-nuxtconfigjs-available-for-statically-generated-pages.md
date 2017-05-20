# Question: Are env vars set in nuxt.config.js available for statically generated pages

## Answer: Yes

```js
//nuxt.config.js
module.exports = {                                                                                                                                                                                                                                            
    env: { testing: process.env.TTT },                                                                                                                                                                                                                        
    ...    
}
```

```js
// pages/index.vue

<template>
  <section class="container">
    <div>
      testing: {{testing}}
    </div>
  </section>
</template>

<script>

export default {
  components: {
    Logo
  },

  computed: {
    testing(){
          return process.env.testing
    }
  },
  mounted () {
    console.log('mounted', this.testing)
  }
}
</script>
```

run generate: `TTT=xxxx npm run generate`

Your statically generated site will now have `process.env.testing` set to xxxx. The template and `console.log('mounted', this.testing)` will also show xxxx.



