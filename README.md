<h2>Overview</h2>
<p>This guide provides a detailed process to set up a Counter-Strike 2 server on your local Linux machine. By following these steps, you'll have your server up and running in no time.</p>

<h2>How It Works</h2>
<p>This setup utilises LinuxGSM (Linux Game Server Managers), a command-line tool for quick, simple deployment and management of dedicated game servers. We'll also be using SteamCMD, a command-line version of the Steam client, to download and update the game server files.</p>

<h2>Prerequisites</h2>
<ul>
    <li>A Linux machine</li>
    <li>Basic knowledge of command-line operations</li>
    <li>An active Steam account for Steam Game Server Token</li>
</ul>

<h2> Setup Instructions </h2>

<h3>Step 1: Add i386 Architecture</h3>
<pre><code>sudo dpkg --add-architecture i386</code></pre>

<h3>Step 2: Update Package List</h3>
<pre><code>sudo apt update</code></pre>

<h3>Step 3: Install Required Packages</h3>
<p>Install all the necessary packages:</p>
<pre><code>sudo apt install mailutils postfix curl wget file tar bzip2 gzip unzip bsdmainutils python3 util-linux ca-certificates binutils bc jq tmux lib32gcc-s1 lib32stdc++6 steamcmd -y</code></pre>

<h3>Step 4: Download and Prepare LinuxGSM</h3>
<p>Download the LinuxGSM script and make it executable:</p>
<pre><code>wget -O linuxgsm.sh https://linuxgsm.sh/ && chmod +x linuxgsm.sh</code></pre>

<h3>Step 5: Install Counter-Strike 2 Server</h3>
<p>Run the LinuxGSM script to install the Counter-Strike 2 server:</p>
<pre><code>bash linuxgsm.sh cs2server</code></pre>

<h3>Step 6: Obtain Steam Game Server Token</h3>
<ol>
    <li>Visit the <a href="https://steamcommunity.com/dev/managegameservers">Steam Game Server Account Management</a> page.</li>
    <li>Log in with your Steam account.</li>
    <li>Create a new game server account with the following details:</li>
    <ul>
        <li><strong>App ID</strong>: <code>730</code> (for Counter-Strike: Global Offensive)</li>
        <li><strong>Memo</strong>: A descriptive name for your server</li>
    </ul>
    <li>Copy the generated login token and add it to your server configuration file.</li>
</ol>

<h3>Step 7: Configure Server</h3>
<p>Edit the server configuration file as needed:</p>
<pre><code>nano /lgsm/config-default/config-game/server.cfg</code></pre>
<p>your config file should look like this:</p>
<pre><code>// hostname - Hostname for server.
hostname "SERVERNAME"

// sv_password - Server password for entry into multiplayer games.
sv_password ""

// sv_setsteamaccount - token Set game server account token to use for logging in to a persistent game server account
// https://steamcommunity.com/dev/managegameservers
sv_setsteamaccount ""

// map - Start playing on specified map.
map "de_anubis"

// mapcyclefile - Name of the .txt file used to cycle the maps on multiplayer servers
mapcyclefile "mapcycle.txt"

// sv_lan - Server is a lan server ( no heartbeat, no authentication, no non-class C addresses ).
sv_lan false

// sv_logfile - Log server information in the log file.
sv_logfile true

// sv_logbans - Log server bans in the server logs.
sv_logbans true

// sv_voiceenable - Enable voice communications.
sv_voiceenable true

// sv_alltalk - Players can hear all other players, no team restrictions.
sv_alltalk false

// game_alias - Set the configuration of game type and mode based on game alias like 'deathmatch'.
// values: casual, deathmatch, competative, wingman
game_alias "casual"

// host_workshop_collection - Host a workshop map collection as a mapgroup.
// e.g host_workshop_collection "3104731381"
host_workshop_collection

// host_workshop_map - Get the latest version of the map and host it.
// e.g host_workshop_map "3075706807"
host_workshop_map

// mp_autoteambalance - Define if the game should automatically balance out teams in teamplay (0: no, default, 1: yes)
mp_autoteambalance true
</code></pre>

<h3>Starting the Server</h3>
<p>After completing the configuration, start your server using the following command:</p>
<pre><code>./cs2server start</code></pre>
<p>Your Counter-Strike 2 server should now be up and running.</p>

<h2>Additional Resources</h2>
<ul>
    <li><a href="https://docs.linuxgsm.com/">LinuxGSM Documentation</a></li>
    <li><a href="https://developer.valvesoftware.com/wiki/SteamCMD">SteamCMD Documentation</a></li>
</ul>

<p>Follow these steps to successfully set up and run your Counter-Strike 2 server on a Linux machine. Happy gaming!</p>
