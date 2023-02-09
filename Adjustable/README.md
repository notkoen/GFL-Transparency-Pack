
# Proxy

To add adjustable transparency to future playermodels, add the following lines/proxies to all Valve Materials Files (`.vmt`) for the player models.

```yaml
    "$alpha" "1.0"
    "$player_distance" "0.0"
    "$hide_dist" "0.0"
    "$same_team" "0"
    "$const_1" "0.5"
    "$const_2" "1"
    "Proxies"
    {
        "ConVar"
        {
            "convar" "hide_dist"            // For transparency distance
            "resultVar" "$hide_dist"
        }
        "PlayerTeamMatch"
        {
            "resultVar" "$same_team"        // 0 different, 1 same team
        }
        "PlayerProximity"
        {
            "scale" "0.007"                 // Fade out/in scale. This is hard set and cannot be based off a ConVar
            "resultVar" "$player_distance"
        }
        "Subtract"
        {
            "srcVar1" "$player_distance"
            "srcVar2" "$hide_dist"          // Subtract from distance. This is based on scale of 1 / playerproximity (ie. 0.07 playerproximity scaling means a 1 here would account for ~143 units of distance).
            "resultVar" "$player_distance"
        }
        "LessOrEqual"
        {
            "srcVar1" "$same_team"          // if $same_team
            "srcVar2" "$const_1"            // <= 0.5
            "resultVar" "$player_distance"  // { $player_distance =
            "LessEqualVar" "$const_2"       // 1 }
            "greaterVar" "$player_distance" // else { $player_distance = $player_distance }
        }
        "Clamp"
        {
            "min" "0"
            "max" "1.0"
            "srcVar1" "$player_distance"
            "resultVar" "$alpha"
        }
    }
```