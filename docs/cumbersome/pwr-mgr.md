
`xfce4-power-manager.xml`
=========================


Confusing key names
-------------------

* `brightness-on-ac` is related to display brightness.
  Can you guess its unit of measurement? Percent maybe?
  No. Obviously, "brightness" means a duration, you noob!
  So it's in seconds, at least for values greater than or equal to 10.
  (For lower values, see below.)



Confusing magic values
----------------------

* Several groups of power saving delays have different units of measurement,
  and different values for "never":
  * `blank-on-ac`: minutes, "never" = `0` (somewhat intuitive)
  * `brightness-on-ac`: seconds, "never" = `9` (because `0` = default)
  * `inactivity-on-ac`: minutes, "never" = `14` (haven't tried what `0` means)
* Button actions like `power-button-action`: They are stored as numbers,
  seemingly ordered by how much power they save immediately.
  Can you guess the mystery item?
  0 = Do nothing, 1 = Suspend, 2 = Hibernate, 3 = ??, 4 = Shutdown.
  Correct! Obviously, the mystery item in this progression is "Ask the user".



Fake options that should not be saved
-------------------------------------

A config file should only store intentional decisions made by users.

* `logind-handle-lid-switch`: The config GUI does not offer the user any
  choice about this. Users cannot make a decision, so no fabrication of a
  decision should be saved.
  (Instead, the config GUI calculates the appropriate value based on other
  settings. No need to save the result of this calculation.)









