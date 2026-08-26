# Daily News Dashboard v2

A local-only Windows desktop dashboard that fetches RSS articles, scores them, saves dated JSON briefs, and displays the best 10 articles in a slim dark interface.

## Run Locally

```powershell
cd C:\Users\gmros\Desktop\Daily-Intelligence-Agent\daily_news_dashboard_v2
python update_brief.py
python run_dashboard.py
```

You can also double-click `launch_dashboard.bat`.

## Daily Scheduling

Run this from PowerShell to create a Windows Task Scheduler job:

```powershell
.\install_daily_task.ps1 -DailyTime "07:30"
```

The scheduled task runs `update_daily_brief.bat`, which saves a dated JSON brief under `data\briefs`.

## Build EXE

```powershell
.\build_exe.ps1
```

The executable is created at `dist\DailyNewsDashboard.exe`. The app stores local data beside the executable when packaged.

## Architecture

- `daily_news_dashboard\pipeline.py`: RSS retrieval, scoring, duplicate removal, article selection, and JSON brief writing.
- `daily_news_dashboard\dashboard_app.py`: Tkinter desktop dashboard.
- `sources.json`: RSS feeds mapped to the four final categories.
- `data\briefs`: historical dated brief files.
- `data\state`: update logs and local state.
