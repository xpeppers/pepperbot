# Pepperbot

This is XPeppers version of GitHub's Campfire bot, hubot. He's pretty cool.

This version is designed to be deployed on [Heroku][heroku] and to work with [Slack][slack].

[heroku]: http://www.heroku.com
[slack]: http://www.slack.com

### Testing Hubot Locally

You can test your hubot by running the following.

    % bin/hubot

You'll see some start up output about where your scripts come from and a
prompt.

    [Sun, 04 Dec 2011 18:41:11 GMT] INFO Loading adapter shell
    [Sun, 04 Dec 2011 18:41:11 GMT] INFO Loading scripts from /home/tomb/Development/hubot/scripts
    [Sun, 04 Dec 2011 18:41:11 GMT] INFO Loading scripts from /home/tomb/Development/hubot/src/scripts
    Hubot>

Then you can interact with hubot by typing `hubot help`.

    Hubot> hubot help

    Hubot> animate me <query> - The same thing as `image me`, except adds a few
    convert me <expression> to <units> - Convert expression to given units.
    help - Displays all of the help commands that Hubot knows about.
    ...


### Scripting

Take a look at the scripts in the `./scripts` folder for examples.
Delete any scripts you think are useless or boring.  Add whatever functionality you
want hubot to have. Read up on what you can do with hubot in the [Scripting Guide](https://github.com/github/hubot/blob/master/docs/scripting.md).

## external-scripts

Tired of waiting for your script to be merged into `hubot-scripts`? Want to
maintain the repository and package yourself? Then this added functionality
maybe for you!

Hubot is now able to load scripts from third-party `npm` packages! To enable
this functionality you can follow the following steps.

1. Add the packages as dependencies into your `package.json`
2. `npm install` to make sure those packages are installed

To enable third-party scripts that you've added you will need to add the package
name as a double quoted string to the `external-scripts.json` file in this repo.

## Deployment

    % heroku create --stack cedar --name pepperbot --region eu
    % git push heroku master
    % heroku ps:scale app=1
    % heroku addons:add redistogo:nano
    % heroku config:add HEROKU_URL={pepperbot url}
    % heroku config:add HUBOT_SLACK_TOKEN={slack token}
    % heroku config:add HUBOT_SLACK_TEAM=xpeppers
    % heroku config:add HUBOT_SLACK_BOTNAME=pepperbot

If you run into any problems, checkout Heroku's [docs][heroku-node-docs].

More detailed documentation can be found on the
[deploying hubot onto Heroku][deploy-heroku] wiki page.

## Restart the bot

You may want to get comfortable with `heroku logs` and `heroku restart`
if you're having issues.
