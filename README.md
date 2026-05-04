# WebHarvest

small devops final project for watching structured data on public web pages

the whole trick is simple

the llm runs once to make a css selector recipe then normal cron polls use beautifulsoup against that cached recipe

so the llm is setup cost not every poll cost

## run it

```sh
cp .env.example .env
```

add `OPENROUTER_API_KEY` in `.env`

```sh
docker compose up --build
```

then open

- app: <http://localhost:3000>
- grafana: <http://localhost:3001/d/webharvest>
- prometheus: <http://localhost:9090>

## demo

1. start the stack
2. open the app
3. pick a preset source
4. hit add and run
5. first run calls the llm and saves anchors
6. next runs should be fast path with no llm call
7. open grafana and show status rate errors duration activity and diagnostics

## whats in here

- `postgres` stores sources runs snapshots entities and field changes
- `scraper` is the fastapi app
- `worker` runs the cron polling loop
- `extracto` wraps openrouter for the one time recipe call
- `dashboard` is the ui
- `prometheus` scrapes metrics
- `grafana` shows the ops dashboard

## more detail

the paper has the full architecture and screenshots

`SWOT_ANALYSIS.md` has the rubric style tool writeup
