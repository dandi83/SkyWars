SkyWars Function Testing
------------------------

This file overviews all the features of SkyWars that need to be tested manually.

This is for use if you want to submit a Pull Request to SkyWars and confirm that it doesn't break anything, or you want to test a development build for yourself.

This basically just lists all the things that are required to consider a SkyWars build "working".

Some things here aren't listed, but are implied by other steps. For instance, there is no reason to test `Confirm you win a game after killing everyone`
if you're already testing `Confirm your score is increased when you win a game`

I may do this differently in the future, but it seems a bit redundant for now.

Before testing:

* Completely wipe all configuration files and worlds
* Install craftbukkit build you're testing for
* Run server once, then stop
* Set online-mode to false in server.properties
* Set allow-nether to false in server.properties
* Set allow-end to false in bukkit.yml
* Delete world_nether and world_the_end
* Install Vault of the version you're testing for
* Install BOSEconomy to test economy
 * BOSEconomy is the most simple economy plugin I've found to test with. If someone else has a better suggestion, I'm open to it!
* Set `economy.enabled` to `true` in `plugins/SkyWars/main-config.yml`
* Add `skywars.kit:\n    default: true` to `permissions.yml` to enable usage of `/sw kit` by non-ops

And now, testing!

* Start two arenas, confirm `/sw cancelall` works
* Start two arenas, confirm `/sw cancel` works on each
* Confirm `/sw cancel` fails with no arenas started
* Confirm `/sw report` works
* Add one person to queue, confirm `/sw forcestart` doesn't work
* Add two people to queue, confirm `/sw forcestart` works
* Join the queue using both the `/sw join` command, and a join portal
* Confirm `/sw kit` lists both available and unavailable kits.
* Apply a kit using `/sw kit`, and confirm it's applied
* Confirm the kit is still applied next game
* Confirm `/sw kit` shows you've applied a kit
* Confirm `/sw kit remove` removes your kit
* Confirm `/sw kit` won't let you apply a kit you don't have permission for
* Confirm `/sw kit` won't let you apply a kit you don't have money for
* Confirm `/sw kit` will apply a kit that does require permission
* Confirm `/sw kit` will apply a kit that doesn't require permissions or money
* Confirm `/sw kit` will apply a kit that costs money, and that your money decreases
* Confirm kit is removed after you run out of money
* Confirm permission kit isn't applied if you loose the permission
* Confirm `/me` isn't blocked in-game
* Confirm `/gamemode` is blocked in-game
* Confirm `/sw leave` works from the queue
* Confirm `/sw leave` works from in-game
* Confirm `/sw lobby` works
* Confirm `/sw lobby` is blocked in-game
* Confirm `/sw setlobby` works, and changes are reflected in `/sw lobby`
* Confirm respawn location after leaving game reflects new lobby
* Confirm `/sw setportal` sets a portal that works
* Confirm `/sw delportal` removes the portal
* Confirm `/sw status` accurately displays both people in queue and running games
* Confirm `/sw status` doesn't display games after they have ended
* Confirm `/sw version` accurately displays plugin version
* Confirm in-game death messages display correctly when someone is directly killed
* Confirm in-game death messages display correctly when someone is pushed into the void
* Confirm in-game death messages display correctly when someone kills themself through drowning
* Confirm your score is increased when you win a game
* Confirm your score is increased when you kill someone
* Confirm your score is decreased when you die in a game
* Confirm your score is unaffected when you die outside of a game
* Confirm you can't hit someone on your team
* Confirm after you kill everyone the game ends
* Config testing:
 * Confirm you keep your inventory after dying with `save-inventory: true`
 * Confirm you loose your inventory after dying with `save-inventory: false`
 * Confirm `/sw help` changes after setting `locale: es` (or any other language)
 * Confirm SkyWars starts up correctly with locale set to `cz`, `de`, `en`, `es`, `fr`, `pt` and `ru`
 * Confirm messages.yml updates after changing locale when auto-update is set to true
 * Confirm messages.new.yml is created after changing locale when auto-update is set to false
 * Confirm messages.yml *does not* update after changing locale when auto-update is set to false
 * Confirm `/sw kit` does not display economy-cost kits after setting `economy.enabled: false`
 * TODO: More encompassing config testing overview
* TODO: Setup testing overview
