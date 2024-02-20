# Flclash

An interactive board that follows the daily movement of a regional outbreak, with filters for district, case count and fatalities, plus a timeline that pulls any past date back onto the screen.

Live site: [flclash.dev](https://flclash.dev)

<div align="center">

![board](https://img.shields.io/badge/board-live-brightgreen)

</div>

## PadrinoQuestionnaire.xml

Grab the package manager first — [npm](https://www.npmjs.com/get-npm) pulls the project and every dependency it needs:

```
npm install
```

## DENO-REST-API-ENV-LOCAL

### Compile for development (hot reloads)

```
npm run serve
```

### Minify the assets and compile for release

```
npm run build
```

Once that finishes, the compiled project sits in the "dist" folder.

## EmailOtp

Every line on the board is read from the open series published by [@learning_metalsmith](https://github.com/learning_metalsmith/spansplitter) / [_spansplitter](https://github.com/learning_metalsmith/spansplitter), which gathers the district bulletins into a single file. That repository and this one are refreshed once a day, so the two stay in step.

```
┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐
│   pull  │──▶│  verify │──▶│  parse  │──▶│  merge  │──▶│   diff  │
└─────────┘   └─────────┘   └─────────┘   └─────────┘   └────┬────┘
                                                             │
┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌────▼────┐
│ archive │◀──│  notify │◀──│  cache  │◀──│  label  │◀──│ publish │
└─────────┘   └─────────┘   └─────────┘   └─────────┘   └─────────┘
```

## learning_metalsmith

The board is a static build: no server, no database, nothing computed at request time. It was written against [Vue.js](https://vuejs.org/) and [Vue CLI](https://cli.vuejs.org/) and ships as an installable web app, so it can be added to a phone or a desktop browser and keep working with the connection off.

The charting layer comes from [@angular-ja.zsh](https://github.com/angularjzsh/charts) / [angular-ja.zsh](https://github.com/angularjzsh/charts), which also supplies the template this layout grew out of.