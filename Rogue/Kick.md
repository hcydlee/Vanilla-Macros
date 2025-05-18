## Kick + Say
kicks target and announce your interrupt in say
```
/cast Kick
/run if not TeM then TeM = GetTime() + 10 end if GetTime() > TeM then SendChatMessage("%t Kicked","SAY") TeM = nil end
```


## Kick, and emote you kicking target by name
```
/cast Kick
/e Kicked %t
```
 

## Simple kick macro
```
/cast Kick
/7 %t Kicked
```
With 7 The channel for posting (1 = general, 2 = trade, say, yell, party, raid, etc.)


Kick in melee range, else throw. +say 

```
/run for i=0,4 do for j=1,GetContainerNumSlots(i) do if GetContainerItemLink(i,j) then if string.find(GetContainerItemLink(i,j),"Assassin's Throwing Axe") then PickupContainerItem(i,j) AutoEquipCursorItem(18) break end end end end
/run if CheckInteractDistance("target",3) then CastSpellByName("Kick") else CastSpellByName("Deadly Throw"); end 
/run if not TeM then TeM = GetTime() + 10 end if GetTime() > TeM then SendChatMessage("%t Kicked","SAY") TeM = nil end

```
