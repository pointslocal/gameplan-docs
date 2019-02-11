# Gameplan Widgets
{{ site.url }}

The Gameplan widget library allows you to create seamless widgets for scoreboards, score tickers and daily leaderboards

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
        teamDisplay: 'name',
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
* ```style``` - modifies the presentation of the widget per the widget type's specification.
* ```bracket_id``` - can show games by numeric bracket id. Also used by the bracket widget to specify the bracket to show.
* ```teamDisplay``` - by default, the widgets will show a team abbreviation. By setting this option to ```name```, it will bypass and show the full school/team name.
* ```api``` - accepts an object that will pass-through any API options to the ```/games```, ```/leaders```, ```/brackets``` or ```/bracketology``` endpoints as documented here: https://pointslocal.readthedocs.io/en/latest/api/

### Widget Types
Available ```widget``` types are:
* Scoreboard - ```scoreboard``` - a full page grid of scores.
* Ticker - ```ticker``` - a smaller widget that enables scrolling through scores automatically or manually.
* Leaders - ```leaders``` - can show daily stat leaders 
* Brackets - ```brackets``` - shows full bracket with games, available as ```stacked``` in order to place both sides of the bracket on top of each other. Typically handles single-elimination, balanced brackets culminating in a sole final game.
* Bracketology - ```bracketology``` - a more expressive bracket format that allows arbitrary number of teams, consolation brackets and unbalanced rounds.

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
![scoreboard]({{ site.url }}/gameplan-docs/assets/scoreboard.png)

## Ticker
The ticker widget shows up to 5 games at a time (on tablet/desktop views) with the ability to scroll through all of the day's available games.
![scoreboard]({{ site.url }}/gameplan-docs/assets/ticker.png)

## Bracket
Brackets have two primary options: the id, specified by ```bracket_id``` and the display style, which can accept ```full``` (default) or ```stacked``` to show the sides of the bracket vertically.

If called via the ```bracketology``` endpoint, the only view is stacked. This view supports consolation rounds, playins and other abnormal tournament designs.

To use any bracket endpoint, the bracket's ID must be specified via the aforementioned ```bracket_id``` parameter or directly, in the API options . An example:

```
    Gameplan.init({
        selector: '#gameplan-bracket',
        widget: 'bracketology',
        api: {
            id: 29
        },
        endpoint: 'bracketology',
        site: '[your site]',
        disableNavigation: false
    });
```

or

```
    Gameplan.init({
        selector: '#gameplan-bracket',
        widget: 'bracket',
        bracket_id: 29,
        endpoint: 'bracketology',
        site: '[your site]',
        disableNavigation: false
    });
```

## Daily Leaders
Shows the top performers in each category with an optional threshold.

## Styling
Sass files are available at https://dist.pointslocal.com/widgets/gameplan/gameplan.zip