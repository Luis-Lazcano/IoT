# platziverse-agent

## Usage

``` js
const PlatziverseAgent = require('platziverse-agent')

const agent = new PlatziverseAgent({
  interval: 2000
})

agent.addMetric('rss', function getRss(){
  return process.memoryUsage().rss;
})

agent.addMetric('promiseMetric', async function getRandomPromise(){
  return Promise.resolve(Math.random());
})

agent.addMetric('callbackMetric', function get randomCallback(){
  setTimeout(() => {
    callback(null, Math.random())
  }, 1000)
})

agent.connect()

//propios
agent.on('connected', handler)
agent.on('disconnected', handler)
agent.on('message', handler)

//Mqtt
agent.on('agent/connected', handler)
agent.on('agent/disconnected', handler)
agent.on('agent/message', payload => {
  console.log(payload)
})

setTimeout(() => agent.disconnect(), 20000)
```