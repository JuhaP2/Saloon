# Perry Saloon

A complete **saloon job** for **RedM** servers running the VORP framework. Employees serve drinks and meals, bill customers and the boss manages staff and the business account.

## Features

- **Serving** – place bottles, glasses and plated meals (main + sides) on tables and the bar, with a placement mode for moving and rotating props. Placed items are synced to every player.
- **Boss menu** – hire and fire employees, deposit and withdraw from the business account.
- **Storage** – a shared cabinet for saloon staff.
- **Billing** – send bills to customers that are paid into the business account.
- **Multiple saloons** – Saint Denis, the Saint Denis theatre and Blackwater are preconfigured; add more in `config.lua`.
- Map blips for every saloon.

## What's included

The `Perry_Saloon` folder contains four resources:

| Resource | Purpose |
| --- | --- |
| `Perry_Saluuna` | The saloon job itself. |
| `Oku_Accounts` | Shared business accounts and hire/fire. |
| `Oku_Laskutus` | Billing system. |
| `qbr-menu` | Menu UI (qbr-menu converted for VORP). |

## Installation

1. Copy the four folders from `Perry_Saloon` into your server's `resources` folder.
2. Import the database tables from `Perry_Saluuna/saluunajne.sql`. Skip the `CREATE DATABASE` / `USE` lines and the sample data if you already have a VORP database.
3. Add them to `server.cfg` after VORP:
   ```cfg
   ensure qbr-menu
   ensure Oku_Accounts
   ensure Oku_Laskutus
   ensure Perry_Saluuna
   ```
4. Create the saloon jobs (`saintdenis`, `cinema`, `bwsaluuna` by default) in your job setup.
5. Restart the server.

## Configuration

Saloons are defined in `Perry_Saluuna/config.lua`:

```lua
Config.Saluunat = {
    ["SaintDenis"] = {
        name = "saintdenis",
        blipname = "Saluuna",
        position = vector3(2639.85, -1227.58, 53.28),  -- serving spot
        kaappi = vector3(2636.92, -1225.0, 59.5),       -- storage cabinet
        paallikko = vector3(2639.81, -1224.78, 59.49),  -- boss menu
        society = "society_saluuna",                    -- business account
        job = "saintdenis"                              -- job name
    },
}
```

The interaction key is set in `Config.keys`, and prompt texts in `Config.Press*` / `Config.Post*`. In-game texts are in Finnish by default.

## Requirements

- RedM server (`rdr3`)
- [VORP Core](https://github.com/VORPCORE/vorp-core-lua) and vorp_inventory
- menuapi (VORP menu)
- mysql-async

## Support

Found a bug or have an idea? [Open an issue](https://github.com/JuhaP2/Saloon/issues).
If this script is useful for your server, a ⭐ on the repo is appreciated!
