Stock
=====

My spreadsheets for analyzing stock and stock options

Use XLQPlus with this spreadsheet. It costs $159. It does not require the more expensive XLQ2. You can get a free 45 day trial.
https://www.qmatix.com/
You also need a data source. Yahoo is free but doesn't do options. I use TD Ameritrade. Interactive Brokers works, too, I've heard.

TDA <-- This is the data source I use with XLQ because I have a TD Ameritrade account. The cell is named "tda".

What the sheets mean and how to use them
========================================

Portfolio
---------
Contains one line for each position I have. In the Shares column I put 100 for an owned call or put and -100 for a written call or put.
Since there are shares and options in the same sheet some of the equations differ so copy the right kind of line to add a new position.
The last column shows how much money I would gain or lose if there were a 1% drop in the share price (change the top cell to another % if you want.)

Exposure
--------
Aggregates the 1% loss column for all the positions in a given ticker and multipies to show what amount of owned shares has an equivalent exposure. Helps me know when I'm over or underexposed to a given ticker.
This is also where I keep track of what Motley Fool says about each stock.

Generator
---------
A tricky one. This is where I try to generate a list of all the options for a given ticker (the option chain). If you can find a better way to do this please tell me.
Set up the ticker and the range of option prices you're interested in at the upper right. Then update the possible option expiration dates by manually changing the red date in cell O21 to the next options Friday not listed among the weeklies above it.
Then it will go search for all the options it can and list them in the left-hand columns. Once it's done and none say "Busy…", click cell C1, press ctrl+A, then ctrl+C, then click cell I1, press ctrl+V to paste, then press and release ctrl, then press V to change your paste to a paste-values-only.
Then press ctrl+A to highlight cells I1:M889. Then sort by column M so that all the rows that have a valid option appear at the top. These rows are the option chain for this stuck.
Messy, right?

Calls ABC
---------
I use these sheets for studying covered calls, diagonal calls, and rolling a call.
Set the ticker symbol in the upper right.
Then copy 99 valid option dates and strike prices from the Generator page, columns I and J, cells 2:100.
Now paste the option dates and prices into cells A2:B100 of the Calls sheet. After pasting with ctrl+V, change it to paste-by-value by press and release ctrl, then press V. This will preserve the conditional formatting in columns A and B.
Once XLQ fills in the bid/ask for each option you can see the time value gain per month in column J and other stats to help you choose the best covered call to write.
Columns N through U only apply to rolling a call or put. To roll, put a "1" in column N on the row for the option you want to buy to close. Make sure no other cell in column N has any value.
Also make sure that every cell in columns A through M has a valid value. None can say "#VALUE!" or the math in columns N through U will not work. It's fine to have multiple rows for the same option, so just fill in any busted lines with some valid date and strike price.
Now you can look at all your rolling options (ha!). Net debit rolls are negative numbers in column P. Choose how much cash you want to roll.
Net credit rolls require looking at colums S and T. S is the return on incremental capital per quarter. You want 50% or higher, and these are highlighted.
T is return on capital per year. This is to make sure you're not fooling yourself by getting a great return on your *incremental* capital, while your already invested capital sits idly with no upside but plenty of downside.

Puts ABC
--------
These sheets are similar to the Calls ABC sheets, but for puts. There is a P in cell W2 and the equations are different. I think column T may be inaccurate for puts.
On the Generator page make sure to change cell Q3 to P when you want puts.

Multileg ABC
------------
This is my masterpiece. It lets you visualize each option leg of a position and your net gain/less with all different final prices at expiration.
You specify a ticker and an expiration date in the cells with green text.
You specify the first two strike prices in cells B 2 and B3. It will figure out the pattern and fill in the rest.
It then fetches the bid/ask prices for calls and puts at the chosen prices for the given expiration date.
Now fill in cells L1:O3 with four options to map. They must all be found in list in columns B:H. Set the quantity to 0 for ones you don't care about.
K4 shows your net price per share price to buy this position.
Columns L through O show your gain/loss for each leg at the given share price at expiration, and column K shows the net for the whole position.
To the right is a hockey stick graph of these columns, with the green line showing your net return.

BCS ABC
-------
Helps analyze Bull Call Spread opportunities
Seet the ticker and for each section, set the expiration date.
Set the lowest two strike prices of interest in B3 and B4
Columns F through I show the cost to buy the BCS that has the owned leg at the given strike price and the written leg $5 through $20 above that.
Columns K through N show the profit if the price at expiration is above the upper leg.

Buy Calls ABC
-------------
Helps choose which call to buy if you expect a given price at expiration with a given probability.
Choose ticker, expiration, and the first two strike prices of interest.
Choose the first two expiration prices in F1 and G1.
It gives you the gain/loss for each strike price and expiration price.
You can choose an expected expiration price and standard deviation.
This feeds back to column C, with an expected value given a $100 investment.

by David K. McAllister
Released under MIT License.
