<!-- README.md -->

<h1 align="center" id="top">League of Legends Analytics</h1>

<h3 align="center">A space for League of Legends analytics projects by <a href="https://x.com/lol_arailla">Arailla</a>, including a curated list of publicly available resources published by the League of Legends community.</h3>

<!-- ABOUT THE REPOSITORY -->
<h2 id="wave-about-this-repository">:wave: About This Repository</h2>

The README of this repository is an attempt to gather all LoL data-related guides, libraries, tutorials, or any other resources that may be of use to a League of Legends Data Analyst.
If you feel like there's any resource that I've missed, please feel free to create a pull request or <a href="https://x.com/lol_arailla">contact me on Twitter/X!</a>

:information_source: This repository has been _heavily inspired_ by the work of Edd Wester on his <a href="https://github.com/eddwebster/football_analytics">Football Analytics Github</a>, which I highly recommend.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- TABLE OF CONTENTS -->
<h2 id="book-table-of-contents">:book: Table of Contents</h2>

<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#wave-about-this-repository">About This Repository</a></li>
    <li><a href="#book-table-of-contents">Table of Contents</a></li>
    <li>
      <a href="#seedling-lol-data-sources">LoL Data Sources</a>
      <ul>
        <li><a href="#ladder-solo-queue-data">Solo Queue Data</a></li>
        <li><a href="#art-static-data">Static Data</a></li>
        <li><a href="#tv-esports-data">Esports Data</a></li>
        <li><a href="#house-lol-client-data">LoL Client Data</a></li>
      </ul>
    </li>
    <li>
      <a href="#books-resources">Resources</a>
      <ul>
        <li><a href="#libraries">Libraries</a></li>
        <li><a href="#tutorials">Tutorials</a></li>
        <li><a href="#written-pieces">Written Pieces</a></li>
        <li><a href="#videos-and-podcasts">Videos and Podcasts</a></li>
        <li><a href="#github-repositories">Github Repositories</a></li>
        <li><a href="#discord-servers">Discord Servers</a></li>
      </ul>
    </li>
  </ol>
</details>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- LOL DATA SOURCES -->
<h2 id="seedling-lol-data-sources">:seedling: LoL Data Sources</h2>

While all data come from the League of Legends servers, you'll need to know how to query different APIs depending on which kind of data you're interested in.
Solo Queue data is available through the Riot official API, while games played on the tournament realms can be accessed in different ways.

<h3 id="ladder-solo-queue-data">:ladder: Solo Queue Data</h3>

Documentation: https://developer.riotgames.com/

- <a href="#libraries">See all related libraries</a>
- <a href="#tutorials">See all related tutorials</a>
- <a href="#github-repositories">See all related open-source projects</a>

<a href="#book-table-of-contents">Back to Contents</a>

<h4 id="collecting-soloq-data">Collecting Data</h4>

> The following links are coming straight from https://riot-api-libraries.readthedocs.io/en/latest/collectingdata.html

Collecting large amounts of match IDs is far from straightforward and requires quite a few requests. If you want to spare yourself a couple of steps, Canisback on the Riot Games Third-Party Developer Community Discord currently <a href="http://canisback.com/matchId/">hosts</a> a list of match IDs that you can use to pull matches from the `matches/{matchId}` endpoints. These lists are provided for free to the community for use and may go down or stop being updated at any time.

You can also use the League endpoints to get lists of ranked summoners. The positional league endpoints provide a paginated list of all summoners in a Tier + Division + Position (e.g., all ranked Diamond II Top laners). Alternatively, Canisback on the Discord currently <a href="http://canisback.com/leagueId/">hosts</a> a list of league IDs that you can use to pull summoners from the `leagues/{leagueId}` endpoints. These lists are provided for free to the community for use and may go down or stop being updated at any time.

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)

<h3 id="art-static-data">:art: Static Data</h3>

Static data comes in extremely handy when you want to
- get a champion name from their ID
- display any game asset
- get champions and item stats

Since the data only changes when a new patch comes out, it's highly recommended for you to implement caching.

`ddragon` is the official CDN where you can retrieve all of this information. However, you might find it quite underwhelming if you're interested in champion and item stats as it only gives you the minimal stats.

DDragon data only changes when a new LoL patch is released, which you can see the availability of in: https://ddragon.leagueoflegends.com/api/versions.json

Documentation: https://developer.riotgames.com/docs/lol

`cdragon` is a massive collection of community-generated files to augment the data in DDragon. You'll find that items and spell descriptions match the ones you'll see when looking at their in-game description.

Documentation: https://riot-api-libraries.readthedocs.io/en/latest/ddragon.html

You can also clone this repository which contains and archives all of the official DDragon content: https://github.com/InFinity54/LoL_DDragon

- <a href="#tutorials">See all related tutorials</a>

<a href="#book-table-of-contents">Back to Contents</a>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)

<h3 id="tv-esports-data">:tv: Esports Data</h3>

Esports Data is about all of the matches played on tournament servers, thus not accessible by the Riot official API.

Riot mentioned that this data would be accessible to the community <a href="https://lolesports.com/article/dev-diary-introducing-the-new-lol-esports-data-portal/bltf694d66e32ce380a">_at some point in the future_</a>, but for now:

<h4 id="lol-data-esports-leaguepedia">Leaguepedia API</h4>

Leaguepedia is one of the few community projects that have been given access to the LoL Data Portal and thus act as a proxy for the public to have access to these matches, as well as aggregated data coming from their own pages.

Documentation: https://lol.fandom.com/wiki/Help:Leaguepedia_API

- <a href="#libraries">See all related libraries</a>
- <a href="#github-repositories">See all related open-source projects</a>

<h4 id="lol-data-esports-oracles-elixir">Oracle's Elixir Dataset</h4>

If you'd rather work with a prebuilt dataset, Oracle's Elixir is the perfect place for you to start as you can download `.csv` files with the biggest leagues' data: https://oracleselixir.com/tools/downloads

<h4 id="lol-data-esports-chinese-matches">Chinese Matches</h4>

Chinese Matches (mainly LPL and LDL) are quite specific as these competitions are not hosted by Riot themselves, and thus the data is not available from the same sources nor format (you'll notice that the data points do not exactly match the ones you get from the other leagues).

Leaguepedia is maintaining a link between the calendar and their lpl.qq link (under the "VODs & Match Links" tournament section), which in turn can be used to fetch the in-game data.

You can see it being called when opening an lpl.qq link, i.e., https://lpl.qq.com/es/stats.shtml?bmid=10413

A full API definition <a href="https://open.tjstats.com/match-auth-app/swagger/v1/index.html">can be found here</a>, but only a fraction of the endpoints can be queried using the token you can find when looking at lpl.qq match pages.

<h4 id="lol-data-esports-data-portal">LoL Data Portal</h4>

While it's not opened to the community as of yet, esports teams from ERL1+ can access it.
They have access to their scrims (private training matches) data as well as all of Riot's matches data, in a very detailed (second per second) manner.

You may have heard of this data as Bayes Esports', which was the previous data provider contracted to Riot. The LoL Data portal is now being operated by GRID Esports. Source: https://esportsinsider.com/2023/11/riot-games-grid-major-data-partnership-acquires-equity-stake

GRID Esports does not provide any open documentation nor data samples.

<h4 id="lol-data-esports-live-data">LoLEsports Live Data</h4>

There is an API used by https://lolesports.com/, but it is not officially supported and may change at any time without warning.
There is some unofficial documentation here, but it might not be accurate or up-to-date https://vickz84259.github.io/lolesports-api-docs/

<a href="#book-table-of-contents">Back to Contents</a>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)

<h3 id="house-lol-client-data">:house: LoL Client Data</h3>

Documentation: https://github.com/Pupix/rift-explorer - An automatically generated documentation of Riot Games LCU API.

<a href="#book-table-of-contents">Back to Contents</a>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

<!-- RESOURCES -->
<h2 id="books-resources">:books: Resources</h2>

<h3 id="libraries">Libraries</h3>

**All languages**
- Riot API Libraries can all be found on https://riot-api-libraries.readthedocs.io/en/latest/libraries.html

**Python**
- [leaguepedia_parser](https://github.com/mrtolkien/leaguepedia_parser) by [Tolki](https://twitter.com/TolkiCasts)

<a href="#book-table-of-contents">Back to Contents</a>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)

<h3 id="tutorials">Tutorials</h3>

**Python**
- [An Introduction to the Riot API](https://www.itero.gg/articles/riot-api) and its [full Youtube playlist](https://www.youtube.com/playlist?list=PL3vL1pnMCbUERqllcwhcvEJbKum-M9zT5) - from itero.gg
- [Extracting League of Legends data with Riot API](https://github.com/Lacerdash/Extracting-League-of-Legends-data-with-Riot-Api)
- [Leaguepedia API](https://www.youtube.com/watch?v=V1DUvpFE_9c) by [Arces](https://x.com/arceslol) - stream replay of a live coding session
- [An introduction to Streamlit and Plotly — using Champions Queue data](https://medium.com/@arailla/an-introduction-to-streamlit-and-plotly-using-champions-queue-data-b2803dff7eb4) by [Arailla](https://x.com/lol_arailla)

**Elixir**
- [Probuild Ex](https://mrdotb.com/posts/probuild-ex-part-one) by [mrdotB](https://x.com/mrdotB) - creating a fully functioning probuild clone in Elixir

**Others**
- [Resolving spells and variables in spell texts](https://hextechdocs.dev/resolving-variables-in-spell-texts/)
- [Map data](https://hextechdocs.dev/map-data/)

<a href="#book-table-of-contents">Back to Contents</a>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)

<h3 id="written-pieces">Written Pieces</h3>

**Blogs**
I couldn't include them all, but Itero.gg has released a lot of articles in their [Esports Analyst Club newsletter](https://www.itero.gg/articles).

- [Predicting and analyzing metagames in League of Legends](https://medium.com/@benjamin.castet/predicting-and-analyzing-metagames-in-league-of-legends-3cedb9439310) by [Xenesis](https://x.com/lol_Xenesis)
- [Rating Performances in Competitive Environment](https://medium.com/@benjamin.castet/rating-performances-in-competitive-environment-fd09089fc466) by [Xenesis](https://x.com/lol_Xenesis)
- [Why is the League of Legends meta so stale?](https://www.itero.gg/articles/why-is-the-league-meta-stale) from itero.gg
- [LoL: How to win your Solo Queue Draft - a statistical analysis of 1M+ games](https://www.itero.gg/articles/draft-sq) from itero.gg
- [LoL: The Best Opportunities for AI in Esports](https://www.itero.gg/articles/best-ai) from itero.gg
- [FlyTracker - A Disambiguation](https://samhine.notion.site/samhine/FlyTracker-A-Disambiguation-cf228401fb2d420d9512abc05cea68e5) by [Sam Hine](https://twitter.com/samhine)

**Papers:**
- [The SIDO Performance Model for League of Legends](https://www.sido.gg/sido-performance-model)
- [An Approach for Team Composition in League of Legends using Genetic Algorithm (2019)](https://www.sbgames.org/sbgames2019/files/papers/ComputacaoFull/198418.pdf)
- [Factor Analysis for behavior analysis](https://drive.google.com/file/d/1o6FcY_anyv7QE86N8dXMdxL2QZdNB26-/view) by [Warock](https://twitter.com/Warock42)

<a href="#book-table-of-contents">Back to Contents</a>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)

<h3 id="videos-and-podcasts">Videos and Podcasts</h3>

- [How to Use Game Data to Win in Esports](https://www.youtube.com/watch?v=VlZFUW1SbR0) by [Evil Geniuses](https://x.com/evilgeniuses)
- [How Data Is Used Within Esports Orgs](https://www.youtube.com/watch?v=SL_35rOxCAU) by [Evil Geniuses](https://x.com/evilgeniuses)
- [Analyst Insider](https://www.youtube.com/playlist?list=PL3vL1pnMCbUFEX1-s8xvSm6lYTxT5hwf-) by [Jack J](https://x.com/JackJGaming)
- [Deep Dive 2021-2023](https://www.twitch.tv/videos/1983931515) by [Beora](https://twitter.com/_Beora)
- :fr: [KC Analyst Q&A](https://www.twitch.tv/videos/2034539997) by [Xenesis](https://twitter.com/lol_Xenesis)

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)

<h3 id="github-repositories">Github Repositories</h3>

Using the Riot Official API:
- [LeagueStats](https://github.com/vkaelin/LeagueStats) - A website for League of Legends summoners' stats by [LeagueStatsGG](https://x.com/LeagueStatsGG)
- [LoL Matchup Optimizer](https://github.com/Max-We/lol-matchup-optimizer/tree/main) by Max-We
- [LoL Tracker](https://github.com/danblock97/lol-stat-tracker) by [danblock](https://danblock.dev/)
- [Riot API Tools](https://github.com/Baeora/riot_api_tools) by [Beora](https://twitter.com/_Beora)
- [ProbuildEx](https://github.com/mrdotb/probuild_ex) - An open open source probuild.
- [LeagueOfReplays](https://github.com/mrdotb/leagueofreplays) - Record & Replay lol games with spectator API.

Using Leaguepedia API:
- [League of Elo](https://github.com/jprMesh/LeagueOfElo) by jprMesh
- [ProRankings](https://github.com/xtevenx/ProRankings) by xtevenx

Using Oracle's Elixir dataset:
- [Match Modeling](https://github.com/MRittinghouse/ProjektZero-LoL-Model/) by ProjektZero

Using Bayes API:
- [Automatic Wards Script](https://github.com/James-Woodland/Wards) by [Zero](https://x.com/ZeroAnalytics)

Organize your replay files (.rofl):
- [ReplayBook](https://github.com/fraxiinus/ReplayBook) by [Fraxiinus](https://x.com/fraxiinus)

Extracting positional data from VODS using computer vision:
- [DeeperLeague](https://github.com/davidweatherall/DeeperLeague) by davidweatherall
- [LoL Automated Video Analyser - LAVA](https://github.com/Steeeephen/LAVA) by Steeeephen

Tools for Google Sheet:
- [Set Images](https://github.com/Baeora/set_images) by [Beora](https://twitter.com/_Beora)

<a href="#book-table-of-contents">Back to Contents</a>

![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/dark.png)

<h3 id="discord-servers">Discord Servers</h3>

- [Riot Games Third Party Developer Community](https://discord.gg/riotgamesdevrel)
- [LoLStaff Analysis](https://discord.gg/uAHbKNKFUf) :brazil: / :es: server organized by [SrVenancio](https://x.com/SrVenancio1)
- [LoL Analyst Community](https://discord.gg/jduM7FzQs6) organized by [Alejandro Flores](https://x.com/AlexFdezFlores)
- [iTero Gaming](https://discord.gg/itero-gaming-686238814749851697) organized by [Jack J](https://x.com/JackJGaming)
- [Oracle's Elixir](https://discord.gg/mkgagJ6nPg) organized by [Tim Sevenhuysen](https://x.com/TimSevenhuysen)
- [GamesOfLegends](https://discord.gg/MQapQmKmDj) organized by [Bynjee](https://x.com/Bynjee)
- [LoL Coach FR](https://discord.gg/rDrXk5SvpJ) :fr: server organized by [Supernova](https://x.com/Coach_Supernova)
- [Analitycy](https://discord.com/invite/7TkAAsbHwV) 🇵🇱 server organized by [Arces](https://twitter.com/arceslol), [Sanchi](https://twitter.com/Sanchi_lol), and [Devilpiotr](https://twitter.com/Devilpiotr1)

<a href="#book-table-of-contents">Back to Contents</a>

This repository isn't endorsed by Riot Games and doesn't reflect the views or opinions of Riot Games or anyone officially involved in producing or managing League of Legends. League of Legends and Riot Games are trademarks or registered trademarks of Riot Games, Inc. League of Legends © Riot Games, Inc.
