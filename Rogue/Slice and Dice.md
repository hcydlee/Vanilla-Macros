## Slice and Dice / Sinister Strike
```
/run local z=0 for i=1,27 do t=UnitBuff("player",i) if (t and strfind(t,"SliceDice")) then z=1 break end end if z==0 and (GetComboPoints()>=1) then CastSpellByName("Slice and Dice") else CastSpellByName("Sinister Strike")end
```


## Slice and Dice / Backstab
```
/run local z=0 for i=1,27 do t=UnitBuff("player",i) if (t and strfind(t,"SliceDice")) then z=1 break end end if z==0 and (GetComboPoints()>=1) then CastSpellByName("Slice and Dice") else CastSpellByName("Backstab")end
```

## Macro to check the buff time. 
seach helpful buff, if slicedice exist, check the timeleft. Only cast slice and dice while it dose not exist or left lefttime <2 s. 
```

/script local f,timeleft=0,0 for i=0,31 do local id,cancel = GetPlayerBuff(i,"HELPFUL"); if(id > -1) then t=GetPlayerBuffTexture(id) if strfind(t,"SliceDice")then f=1 timeleft = GetPlayerBuffTimeLeft(id); break end end end if (f==0 or timeleft<2) and GetComboPoints("target")>0  then CastSpellByName("Slice and Dice") end



```
