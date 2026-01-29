# Chat-Processor

A fork of [KiethGDR's plugin](https://forums.alliedmods.net/showthread.php?t=286913).

A Sourcemod plugin which allows other plugins to add and manage chat related features.

## Installation

- Add the compiled plugin `chat-processor.smx` to `tf/addons/sourcemod/plugins/`.
- Add the addon configuration file `chat_processor.cfg` to `/tf/addons/sourcemod/configs/`.
- Reload all plugins or restart the server.

## Configuration

The plugin automatically generates a new configuration file `tf/cfg/sourcemod/plugin.chat_processor.cfg` if one does not already exist.

```
// Add GOTV client to recipients list. (Only effects games with GOTV or SourceTV)
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_addgotv "1"

// Allows both teams to communicate with each other through team chat.
// (0 = off, 1 = on)
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_allchat "0"

// Flags required to use the color name and message. Needs sm_chatprocessor_strip_colors 1
// -
// Default: "b"
sm_chatprocessor_colors_flag "b"

// Name of the message formats config.
// -
// Default: "configs/chat_processor.cfg"
sm_chatprocessor_config "configs/chat_processor.cfg"

// Controls how dead communicate.
// (0 = off, 1 = on)
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_deadchat "1"

// Default setting to give forwards to process colors.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_process_colors_default "1"

// Default setting to give forwards to remove colors.
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_remove_colors_default "0"

// Restricts all chat for the dead entirely.
// (0 = off, 1 = on)
// -
// Default: "0"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_restrictdeadchat "0"

// Allow spectators to chat to the teams or just to each other.
// (0 = off, 1 = on)
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_specchat "1"

// Status of the plugin.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_status "1"

// Remove color tags from the name and the message before processing the output.
// -
// Default: "1"
// Minimum: "0.000000"
// Maximum: "1.000000"
sm_chatprocessor_strip_colors "1"
```
There is an additional configuration file `tf/addons/sourcemod/configs/chat_processor.cfg`:

```
"chat-processor"
{
	"csgo"
	{
		"Cstrike_Chat_CT_Loc"	"(Counter-Terrorist) {1} : {2}"
		"Cstrike_Chat_CT"	"(Counter-Terrorist) {1} : {2}"
		"Cstrike_Chat_T_Loc"	"(Terrorist) {1} : {2}"
		"Cstrike_Chat_T"	"(Terrorist) {1} : {2}"
		"Cstrike_Chat_CT_Dead"	"*DEAD*(Counter-Terrorist) {1} : {2}"
		"Cstrike_Chat_T_Dead"	"*DEAD*(Terrorist) {1} : {2}"
		"Cstrike_Chat_Spec"	"(Spectator) {1} : {2}"
		"Cstrike_Chat_All"	"{1} : {2}"
		"Cstrike_Chat_AllDead"	"*DEAD* {1} : {2}"
		"Cstrike_Chat_AllSpec"	"*SPEC* {1} : {2}"
	}
	
	"csco"
	{
		"Cstrike_Chat_CT_Loc"	"(Counter-Terrorist) {1} : {2}"
		"Cstrike_Chat_CT"	"(Counter-Terrorist) {1} : {2}"
		"Cstrike_Chat_T_Loc"	"(Terrorist) {1} : {2}"
		"Cstrike_Chat_T"	"(Terrorist) {1} : {2}"
		"Cstrike_Chat_CT_Dead"	"*DEAD*(Counter-Terrorist) {1} : {2}"
		"Cstrike_Chat_T_Dead"	"*DEAD*(Terrorist) {1} : {2}"
		"Cstrike_Chat_Spec"	"(Spectator) {1} : {2}"
		"Cstrike_Chat_All"	"{1} : {2}"
		"Cstrike_Chat_AllDead"	"*DEAD* {1} : {2}"
		"Cstrike_Chat_AllSpec"	"*SPEC* {1} : {2}"
	}
	
	"cstrike"
	{
		"Cstrike_Chat_CT_Loc"	"(Counter-Terrorist) {1}{3} : {2}"
		"Cstrike_Chat_CT"	"(Counter-Terrorist) {1}{3} : {2}"
		"Cstrike_Chat_T_Loc"	"(Terrorist) {1}{3} : {2}"
		"Cstrike_Chat_T"	"(Terrorist) {1}{3} : {2}"
		"Cstrike_Chat_CT_Dead"	"*DEAD*(Counter-Terrorist) {1}{3} : {2}"
		"Cstrike_Chat_T_Dead"	"*DEAD*(Terrorist) {1}{3} : {2}"
		"Cstrike_Chat_Spec"	"(Spectator) {1}{3} : {2}"
		"Cstrike_Chat_All"	"{1}{3} : {2}"
		"Cstrike_Chat_AllDead"	"*DEAD* {1}{3} : {2}"
		"Cstrike_Chat_AllSpec"	"*SPEC* {1}{3} : {2}"
	}
	
	"left4dead"
	{
		"L4D_Chat_Infected"	"(Infected) {1} : {2}"
		"L4D_Chat_Survivor"	"(Survivor) {1} : {2}"
		"L4D_Chat_Infected_Dead"	"*DEAD*(Infected) {1} : {2}"
		"L4D_Chat_Survivor_Dead"	"*DEAD*(Survivor) {1} : {2}"
		"L4D_Chat_Spec"	"(Spectator) {1} : {2}"
		"L4D_Chat_All"	"{1} : {2}"
		"L4D_Chat_AllDead"	"*DEAD* {1} : {2}"
		"L4D_Chat_AllSpec"	"*SPEC* {1} : {2}"
	}
	
	"left4dead2"
	{
		"L4D_Chat_Infected"	"(Infected) {1} : {2}"
		"L4D_Chat_Survivor"	"(Survivor) {1} : {2}"
		"L4D_Chat_Infected_Dead"	"*DEAD*(Infected) {1} : {2}"
		"L4D_Chat_Survivor_Dead"	"*DEAD*(Survivor) {1} : {2}"
		"L4D_Chat_Spec"	"(Spectator) {1} : {2}"
		"L4D_Chat_All"	"{1} : {2}"
		"L4D_Chat_AllDead"	"*DEAD* {1} : {2}"
		"L4D_Chat_AllSpec"	"*SPEC* {1} : {2}"
	}
	
	"tf"
	{
		"TF_Chat_Team_Loc"	"(TEAM) {1} : {2}"
		"TF_Chat_Team"	"(TEAM) {1} : {2}"
		"TF_Chat_Team_Dead"	"*DEAD*(TEAM) {1} : {2}"
		"TF_Chat_Spec"	"(Spectator) {1} : {2}"
		"TF_Chat_All"	"{1} : {2}"
		"TF_Chat_AllDead"	"*DEAD* {1} : {2}"
		"TF_Chat_AllSpec"	"*SPEC* {1} : {2}"
		"TF_Chat_Coach"	"(Coach) {1} : {2}"
	}
	
	"tf2classic"
	{
		"TF_Chat_Team_Loc"	"(TEAM) {1} : {2}"
		"TF_Chat_Team"	"(TEAM) {1} : {2}"
		"TF_Chat_Team_Dead"	"*DEAD*(TEAM) {1} : {2}"
		"TF_Chat_Spec"	"(Spectator) {1} : {2}"
		"TF_Chat_All"	"{1} : {2}"
		"TF_Chat_AllDead"	"*DEAD* {1} : {2}"
		"TF_Chat_AllSpec"	"*SPEC* {1} : {2}"
	}
	
	"hl2mp"
	{
		"HL2MP_Chat_Team_Loc"	"(TEAM) {1} : {2}"
		"HL2MP_Chat_Team"	"(TEAM) {1} : {2}"
		"HL2MP_Chat_Team_Dead"	"*DEAD*(TEAM) {1} : {2}"
		"HL2MP_Chat_Spec"	"(Spectator) {1} : {2}"
		"HL2MP_Chat_All"	"{1} : {2}"
		"HL2MP_Chat_AllDead"	"*DEAD* {1} : {2}"
		"HL2MP_Chat_AllSpec"	"*SPEC* {1} : {2}"
	}
}
```
