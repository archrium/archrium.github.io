---
title: Macro Library
lang: en
authors: Ilke
draft: false
---


### General Macros 

**Random Announce Macro [Requires additional macros]**
```lua
/run local p="xAnn" RunScript(GetMacroBody(p..math.random(1,4)))
```

**Mount flying in flyable zone otherwise normal**
```lua
#showtooltip
/use [flyable, nomounted,nomod] swift blue gryphon; [nomounted,nomod]swift white steed;[mod:alt,nomounted]swift white steed;
/dismount [mounted]
```

**Sells all grays while your npc windows is open**
```lua
/run local c,i,n,v=0;for b=0,4 do for s=1,GetContainerNumSlots(b)do i={GetContainerItemInfo(b,s)}n=i[7]if n and string.find(n,"9d9d9d")then v={GetItemInfo(n)}q=i[2]c=c+v[11]*q;UseContainerItem(b,s)print(n,q)end;end;end;print(GetCoinText(c))
```

**Change gear and spec with single click (Click once again after spec is changed)**
```lua
/stopmacro [combat]
/equipset [spec:1] Primary; Secondary
/usetalents [spec:1] 2; 1
```

**Switch your tab key between TargetNearestEnemy to NearestEnemy**
```lua
/run local T,t,P,m="TargetNearestEnemy","TAB","Player"," is now set to "if GetBindingAction(t)==T then SetBinding(t,T..P)print(t..m..T..P)else SetBinding(t,T)print(t..m..T)end
```

**Set raid target with [skull]**
```lua
/run SetRaidTarget("target",8)
```

**Set Max Camera Distance**
```lua
/script SetCVar("cameraDistanceMax",50)
```

**Link for sell announcement for item in certain bag slot**
```lua
/run SendChatMessage("WTS "..GetContainerItemLink(0,8).." 69g OBO","say",nil,1)
```

### Death Knight


### Druid

**Cast Intervene on Focus if there is no target cast on himself/herself**
```lua
#showtooltip
/cast [@focus,help,nodead][]innervate;
```

### Hunter


### Mage


### Paladin
**Use crusader aura when cast mount, use devotion aura when in combat**
```lua
#showtooltip swift white steed
/cast [nocombat,nomounted,outdoors] !crusader aura;
/use [flyable, nomounted,nomod] golden gryphon; [nomounted,nomod]charger;[mod:alt,nomounted]charger;
/cast [mounted][combat][indoors] !devotion aura;
/dismount [mounted];
```

**Aura talent, mount switch**
```lua
#showtooltip
/cancelaura divine plea
/cast [nomounted,spec:1] !devotion aura;
/cast [nomounted,spec:2] !concentration aura;
/cast [mounted] !crusader aura;
```

**Target help / harm switch**
```lua
#showtooltip
/cast [mod:alt,@player,help,nodead]flash of light;
/cast [harm]judgement of light;
/target mouseover
/cast [@mouseover,exists,help,nodead][nomod]flash of light;
```


### Priest
**Target mouseover and cast shield on target otherwise on self**
```lua
#showtooltip power word: shield
/target mouseover
/cast [nomod,@mouseover,help]Power Word: Shield;[mod:alt,@player,help]Power Word: Shield;
```

**Slightly Different version of upper macro you can use it to damage your enemies too**
```lua
#showtooltip penance
/target mouseover
/cast [nomod,@mouseover,help][nomod]penance;[mod:alt,@player,help]penance;
```

**Cast PI on priority mouseover > focus > self**
```lua
#showtooltip power infusion
/cast [@mouseover,help,nomod][@focus,exists,nodead,nomod] power infusion;
/cast [@player,help,mod:alt] power infusion;
```

**Inner Focus & Greater Heal**
```lua
#showtooltip inner focus
/cast Inner Focus
/cast [@mouseover] greater heal
```

**Use Binding Heal on mouseover else focus**
```lua
#showtooltip
/target mouseover
/cast [nomod,@mouseover,help][nomod,@focus,exist,nodead,help] binding heal;
```

**Adaptive macro changes fuction on target condition friend/enemy**
```lua
#showtooltip
/cast [harm] Shadow Word: Death;
/target mouseover
/cast [@mouseover,exists,help,nodead][nomod]Renew;[mod:alt,@player,help,nodead]renew;
```

### Rogue

### Shaman

**Cure Different Specs [TemplateScript-Orth]**
```lua
#showtooltip
/cast [mod:alt,help,@player,spec:2] cleanse spirit;
/cast [@mouseover,help,spec:2][spec:2] cleanse spirit;
/cast [mod:alt,help,@player,spec:1] cure toxins;
/cast [@mouseover,help,spec:1][spec:1] cure toxins;
```

**Enhance Weapons Single Button**
```lua
#showtooltip
/castsequence reset=5 Windfury Weapon, Flametongue Weapon;
/castsequence reset=5 16, 17;
/click StaticPopup1Button1
```


### Warlock


### Warrior
**PvP/PvE Spec Alteration**
```lua
#showtooltip
/cast [nomod]heroic strike;
/cast [nomod,spec:2]mortal strike;
/cast [mod:alt,spec:1]cleave;
/cast [mod:alt,stance:1/3,spec:2]piercing howl; [mod:alt,stance:2,spec;2]battle stance;
/startattack
```

**Initial attack macro for Fury PvE**
```lua
#showtooltip
/startattack
/cast bloodthirst
```