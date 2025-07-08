# ps-vue-3.5

## First task

Создать базовый проект Vue.

- Развернуть проект
- Удалить лишние CSS стили
- Удалить все компоненты кроме App.vue
- В App.vue вывести текущую дату в шаблоне
  Отправьте Pull Request

```bash
npm install -D eslint-plugin-vue @vitejs/plugin-vue @vue/eslint-config-prettier eslint
```

## Second task

- Header component
- Score component (props count)
- Card component (event rotation and status changes)

## Third task reactive

- ref для храниния очков
- ref для хранения карт
    - word
    - translation
    - state-closed | opened
    - status-success | fail | pending
- вывести одну любую карту

## Forth task templates and models

- Card with all states
- Output two cards at least

## Fifth task Life Cycle

API integration

- Start local API server (http://localhost:8080/api/random-words)
- Download data from API for cards
- Add cards to the state
- Display cards in the template

## Sixth task

- event rotate
- event successful answer
- if success plus 10 points, if mistake take 4 points
- make button Start again - loads new data

