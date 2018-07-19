# Gameplan Widgets
{{ site.url }}

The Gameplan widget library allows you to create seamless widgets for scoreboards, score tickers, leaders and 

> Note: as of the Fall 2018 widgets release, browser compatibility requirements have changed for Gameplan. jQuery is no longer a requirement, Supported modern browsers include: 
* Microsoft Edge
* Internet Explorer >= v11
* Chrome >= v66
* Chrome for Android >= v67
* Firefox >= v60
* Safari >= 11.1
* iOS Safari >= 10.3.

## Configuration
To start, you'll need a discrete target DOM element"

```html
<div id="scoreboard"></div>
```

Then pull in the core Gameplan library
```html
<script src="https://dist.pointslocal.com/widgets/gameplan/main.js"></script>
```

Finally on page loaded, initialize the widget:
```html
<script>
    Gameplan.init({
        selector: '#scoreboard',
        widget: 'scoreboard',
        site: '[site]',
        date: '[date]',
        sid: [sport_id],
        disableNavigation: false,
    });
</script>
```

### Options
* ```selector``` - the DOM selector for targeting the widget.
* ```widget``` - the type of widget to show. See Widget Types.
* ```site``` - your Pointslocal-supplied site code.
* ```date``` - (optional), a start date for the games. Defaults to today.
* ```sid``` - a sport's internal ID from Pointslocal. 
* ```disableNavigation``` - will hide the day and sports navigation from above the widget.
* ```leaders``` - an object of stats to highlight.  See Leaders.

### Widget Types
Available ```widget``` types are:
* Scoreboard - a full page grid of scores.
* Ticker - a smaller widget that enables scrolling through scores automatically or manually.
* Leaders - can show daily stat leaders 

### Leaders 
Will show the top-performing players of the day based on specified stat types. This takes an object of stats and optional minimums and counts. Without a count, it will show 2 maximum players.

Example:
```json
[
  { "stat": "rushing-yards", "minimum": 50, "count": 5 },
  { "stat": "passing-yards", "minimum": 100, "count": 5 },
  { "stat": "receiving-yards", "minimum": 25, "count": 3 }
]
```


## Scoreboard
The scoreboard shows a full page of a day's games in a grid format. 

## Ticker
The ticker widget shows up to 5 games at a time (on tablet/desktop views) with the ability to scroll through all of the day's available games.

## Daily Leaders
Shows the top performers in each category with an optional threshold.

## Styling
Sass files are available at https://dist.pointslocal.com/widgets/gameplan/gameplan.zip