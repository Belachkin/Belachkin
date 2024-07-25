
![](https://github.com/Belachkin/Belachkin/blob/main/assets/header.gif)
# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: belachkin
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Europe/Moscow
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          plugin_screenshot: yes
          plugin_screenshot_background: yes
          plugin_screenshot_mode: image
          plugin_screenshot_selector: section.section centered-content
          plugin_screenshot_title: Screenshot
          plugin_screenshot_url: https://yandex.ru/games/developer/48317
          plugin_screenshot_viewport: {
  "width": 1280,
  "height": 1280
}


