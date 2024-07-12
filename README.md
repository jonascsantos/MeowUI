# MeowUI

<img src="https://meow.jonascsantos.com/meow.gif" alt="MeowGif" width="200" height="200"/>

Fetch images from CATAAS through a UI

MeowUI App | [https://meow.jonascsantos.com/](https://meow.jonascsantos.com/)

MeowAPI | [https://meowapi.jonascsantos.com/cat](https://meowapi.jonascsantos.com/cat)

## Figma

[Design](https://www.figma.com/design/wCSiNRrmqABQHtnFbIq8aD/MeowAPI?node-id=1203-39&t=2OlqP3clwAzoHYv6-1)

[Prototype](https://www.figma.com/proto/wCSiNRrmqABQHtnFbIq8aD/MeowAPI?node-id=1208-3166&t=i1TfuTf7YWOZCT9q-1&scaling=scale-down&content-scaling=fixed&page-id=1203%3A39&starting-point-node-id=1208%3A3166&show-proto-sidebar=1)

## Technologies  

* Vue.js
* Python
* Flask
* Azure
* Figma
* 
## Running locally

### Vue App

Dev environment
```sh
npm run dev
```
or
```sh
vite --host
```

### Python Flask API
```sh
docker-compose build
docker-compose up
```

## Example URLs

Blur:
https://meowapi.jonascsantos.com/cat?filter=blur&blur=20

Mono:
https://meowapi.jonascsantos.com/cat?filter=mono

Sepia:
https://meowapi.jonascsantos.com/cat?filter=sepia

Negative:
https://meowapi.jonascsantos.com/cat?filter=negative

Paint:
https://meowapi.jonascsantos.com/cat?filter=paint&r=7&g=12&b=50

Pixel:
https://meowapi.jonascsantos.com/cat?filter=pixel&pixel=10




