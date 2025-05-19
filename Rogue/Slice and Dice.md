## Slice and Dice / Sinister Strike
```
/run local z=0 for i=1,27 do t=UnitBuff("player",i) if (t and strfind(t,"SliceDice")) then z=1 break end end if z==0 and (GetComboPoints()>=1) then CastSpellByName("Slice and Dice") else CastSpellByName("Sinister Strike")end
```


## Slice and Dice / Backstab
```
/run local z=0 for i=1,27 do t=UnitBuff("player",i) if (t and strfind(t,"SliceDice")) then z=1 break end end if z==0 and (GetComboPoints()>=1) then CastSpellByName("Slice and Dice") else CastSpellByName("Backstab")end
```

## Macro to check the buff time. 
```

/run for i=0,31 do local id,cancel = GetPlayerBuff(i,"HELPFUL|HARMFUL|PASSIVE"); if(id > -1) then local timeleft = GetPlayerBuffTimeLeft(id); DEFAULT_CHAT_FRAME:AddMessage(timeleft); end end
```
