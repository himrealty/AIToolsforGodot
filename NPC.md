# 🤖 NPC AI - FREE VERSION for Godot 4
**AI-powered conversational NPCs with voice — plug and play.**

---

## ✅ What's included (Free)
| Feature | Free | Pro |
|---|---|---|
| AI Provider | Gemini only | Gemini + Groq + OpenRouter |
| Voice | VoiceRSS (350 req/day) | ElevenLabs + Google TTS |
| Messages per conversation | 5 max | Unlimited |
| Multiplayer sync | ❌ | ✅ |
| Conversation history | Last 5 only | Full history |
| Model selection | ❌ | ✅ Switch models live |

---

## 🚀 Quick Setup (5 minutes)

### Step 1 — Get your free API keys
- **Gemini** (AI brain): https://aistudio.google.com/ → "Get API Key" → Free tier is generous
- **VoiceRSS** (voice): https://www.voicerss.org/ → Register → 350 free requests/day

### Step 2 — Add to your project
1. Copy `NPC_AI_Free/` folder into your Godot project
2. Open `NPC_AI_Free_Demo.tscn` to see a working example
3. Or add `NPC_AI_Free.gd` as a script to your own `CharacterBody3D`

### Step 3 — Configure in Inspector
Select your NPC node and fill in:
- `Gemini Api Key` → your Gemini key
- `Voicerss Api Key` → your VoiceRSS key  
- `Npc Name` → whatever you want your NPC to be called
- `Npc Personality` → describe your NPC's personality and role
- `Enable Voice` → toggle voice on/off

### Step 4 — Input Map
Go to **Project → Project Settings → Input Map** and add:
- Action name: `interact`
- Key: `E`

### Step 5 — Player setup
Make sure your player `CharacterBody3D` is added to the **"player"** group:
- Select your Player node → Node panel → Groups → Add "player"

---

## 🎮 How it works in-game
1. Player walks near the NPC (enters the interaction Area3D)
2. "Press E to talk with [Name]" prompt appears
3. Player presses E → chat UI opens
4. Player types messages → Gemini responds → VoiceRSS speaks the reply
5. After 5 messages → upgrade prompt appears

---

## 🔧 Customization

### Change NPC personality
```gdscript
# In Inspector → Npc Personality field:
"You are Marcus, a grumpy old blacksmith in a medieval town.
You talk about swords, armor, and complain about your bad knees.
Keep responses short and in-character."
```

### Connect to your own UI
The NPC creates its own chat UI automatically. To use your own:
Override `_create_chat_ui()` in a subclass.

### Trigger conversation from code
```gdscript
# Get reference to your NPC and call:
$NPC._start_conversation()

# End it:
$NPC._end_conversation()

# Damage the NPC:
$NPC.take_damage(25)
```

### Interaction area size
Select `NPC/InteractionArea/AreaCollision` and adjust the `CapsuleShape3D` radius to change how close the player needs to be.

---

## 📁 File structure
```
NPC_AI_Free/
├── NPC_AI_Free.gd          # Main NPC script — attach to CharacterBody3D
├── NPC_AI_Free_Demo.tscn   # Demo scene with placeholder mesh
└── README.md               # This file
```

---

## ⚠️ Known limitations (Free version)
- Only Gemini Flash 1.5 model
- VoiceRSS has a 350 request/day cap on free tier
- No multiplayer synchronization
- Max 5 messages per conversation session
- Emoji cleaning list is basic (limited set)

---

## ⭐ Upgrade to Pro
Pro version includes:
- **Groq** (ultra-fast LLaMA models)
- **OpenRouter** (access 50+ models with fallback)
- **ElevenLabs** (premium realistic voices)
- **Google TTS** (unlimited free voices)
- **Multiplayer sync** via Godot MultiplayerAPI
- **Unlimited conversation history**
- **Live model switching** in-game
- **Priority support**

---

## 🐛 Troubleshooting

**NPC doesn't respond:**
- Check Gemini API key is set correctly in Inspector
- Check Output panel for error messages
- Make sure player is in the "player" group

**No voice:**
- Check VoiceRSS API key is set
- Make sure `Enable Voice` is checked in Inspector
- VoiceRSS free tier is 350 req/day — check if you've hit the limit

**Chat UI doesn't appear:**
- Make sure the `interact` action is mapped in Input Map
- Player must be inside the InteractionArea

**Animation errors:**
- Check that your AnimationPlayer has animations named to match the export vars
- Default names: `Idle`, `Walking`, `Talking`, `Death`
- Change the export vars in Inspector to match your actual animation names

---

Made with ❤️ for the Godot community.
