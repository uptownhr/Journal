# Question: Are dynamic data generated with the static site

## Answer: Yes

Dynamic data defined to load before components are created will be apart of the generated static files. For example, when using `asyncData` - any remote data call will also be performed before and included as part of the generation of the static files.

```js
import axios from 'axios'

export default {
  async asyncData () {
    let res = await axios.get('http://api.startuptabs.com/feed')

    return {
      startups: res.data
    }
  }
}
```



