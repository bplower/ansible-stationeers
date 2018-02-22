# Stationeers

A role for creating [Stationeers](https://stationeers.com/) servers.

## Requirements

No requirements

## Role Variables

There are currently 3 (soon to be 4) groups of variables. All available
variables and their default values are listed here. Further details are below.

```
service_name: stationeers
service_user: stationeers
service_group: stationeers
service_description: Dedicated Stationeers server
service_restart_permitted: yes
accept_steamcmd_license: no
stationeers_default_servername: Stationeers
stationeers_default_gameport: 27500
stationeers_default_updateport: 27015
stationeers_default_password:
stationeers_default_mapname: BASE
stationeers_default_description: Stationeers
stationeers_default_maxplayers: 30
stationeers_default_rconpassword: stationeers
```

### Service Variables

- Variable: `service_name`<br>
  Default: `stationeers`<br>
  Comments:<br>
  The name of the service to create.

- Variable: `service_name`<br>
  Default: `stationeers`<br>
  Comments:<br>
  The user the service should be run as.

- Variable: `service_group`<br>
  Default: `stationeers`<br>
  Comments:<br>
  The group the service user should be a member of.

- Variable: `service_description`<br>
  Default: `Dedicated Stationeers server`<br>
  Comments:<br>
  A description about the Stationeers server to add to the service file.

### SteamCMD Variables

- Variable: `accept_steamcmd_license`<br>
  Default: `no`<br>
  Comments:<br>
  Accepts the SteamCMD license agreement. This role will fail unless you set
  this value to `true` or `yes`.

### Stationeers Default.ini Variables

These settings are all applied to the default.ini file. <!--Several of these
settings will overlap with runtime configurations (which I haven't implemented
quite yet). In most cases, using either will be fine, but setting the default
values will apply to all instances of Stationeers servers while the runtime
configuration apply only to the specific instance of the server.-->

- Variable: `stationeers_default_servername`<br>
  Default: `Stationeers`<br>
  Comments:<br>
  The server name presented in-game

- Variable: `stationeers_default_gameport`<br>
  Default: `27500`<br>
  Comments:<br>
  The port to run the server on

- Variable: `stationeers_default_updateport`<br>
  Default: `27015`<br>
  Comments:<br>

- Variable: `stationeers_default_password`<br>
  Default: <br>
  Comments:<br>

- Variable: `stationeers_default_mapname`<br>
  Default: `BASE`<br>
  Comments:<br>
  The name of the map to load

- Variable: `stationeers_default_description`<br>
  Default: `Stationeers`<br>
  Comments:<br>
  The description of the server presented in-game

- Variable: `stationeers_default_maxplayers`<br>
  Default: `30`<br>
  Comments:<br>
  Maximum number of simultaneous players

- Variable: `stationeers_default_rconpassword`<br>
  Default: `stationeers`<br>
  Comments:<br>
  Password to accept for rcon management

## Example Playbooks
-----------------

The most simple working example of this role is:

```
---
- name: Create Stationeers server
  hosts: localhost
  roles:
  - role: bplower.stationeers
    accept_steamcmd_license: yes

```

SteamCMD requires accepting a license agreement during installation. I will not
presume to make potentially legally binding decisions on your behalf, so
acceptence of this license agreement is noted by the `accept_steamcmd_license`
variable. If you do not provide an affirmative value, you will see the following
error message:

```
TASK [bplower.stationeers : Check SteamCMD license agreement] ******************
fatal: [default]: FAILED! => {"changed": false, "failed": true, "msg": "You must accept the SteamCMD license by setting the variable 'accept_steamcmd_license: true'"}
```

You can set the rconn password via the default.ini settings:

```
---
- name: Create Stationeers server
  hosts: localhost
  roles:
  - role: bplower.stationeers
    accept_steamcmd_license: yes
    stationeers_default_rconpassword: MySuperSecurePassword
```

## License

MIT

## Author Information

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
