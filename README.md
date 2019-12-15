# coding-challenge

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your unit tests
```
npm run test:unit
```

### Lints and fixes files
```
npm run lint
```


#Candidate's doc
I could have chosen Vuex for state-management but decided not to because it would be kind of an overload for a single thing to pass between components.
For limiting text length I declared a Filter globally on the Vue-App so I can reuse it if needed.

Axios was chosen because I worked with it before and I prefer it over fetch (better browser support, less boilerplate).

I lost some time because I intended to use Github-Jobs API but then got into CORS-Issues.
For testing components I installed Jest with the Vue-CLI when setting up but, as I haven't written any tests before, it would have taken some time to read through the docs and watch a video or two. It is a topic I want to expand my knowledge further on tough.
If I had more time I would have written some things to be better reusable. For example less focused naming on it's content and rather on it's behavior.
Additionally I might have structured my SCSS better with use of variables and it's own files where it makes sense.

