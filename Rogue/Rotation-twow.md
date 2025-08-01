# New Turtle WoW Rogue Rotation Macros.
## Superise Attack if possible. If target's target is player, cast Ghostly Strike. If Blade Flurry, and energy low, use Tea, use Juju Flurry and trinket. Low health, use healthstone,healing potion, tea with sugar,  whipper root tuber accordingly. 

```
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (string.find(n,"Gressil, Dawn of Ruin") )then PickupContainerItem(b,s)EquipCursorItem(16)break end end end
/run SnD=false for i=0,31,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run BlF=false for i=0,31,1 do gpb1=GetPlayerBuff(i,"HELPFUL"); if not (gpb1 == -1) and (strfind(GetPlayerBuffTexture(gpb1), "Ability_Warrior_PunishingBlow")) then BlF=true end end
/run AdR=false for i=0,31,1 do gpb2=GetPlayerBuff(i,"HELPFUL"); if not (gpb2 == -1) and (strfind(GetPlayerBuffTexture(gpb2), "Spell_Shadow_ShadowWordDominate")) then AdR=true end end


/run if UnitHealth("target")==0 and UnitExists("target") then ClearTarget(); end
/run if GetUnitName("target")==nil then TargetNearestEnemy(); end

/run for z=1,172 do if IsAttackAction(z) then if not IsCurrentAction(z) then UseAction(z);end;end;end;

/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"SliceDice")then f=1 s=GetPlayerBuffTimeLeft(b) end end end if (f==0 or s<2)  then CastSpellByName("Slice and Dice")  elseif s>2 and GetComboPoints("target")>4 then CastSpellByName("Eviscerate()") elseif (not AdR) and s>10 and GetComboPoints("target")>2   then CastSpellByName("Eviscerate()") elseif AdR and s>4 and GetComboPoints("target")>2   then CastSpellByName("Eviscerate()") end

/run if IsUsableAction(60) and (not AdR) and UnitMana("Player")<81 then CastSpellByName("Surprise Attack()"); end
/run if IsUsableAction(60) and UnitMana("Player")<61 then CastSpellByName("Surprise Attack()"); end

/run if UnitExists("target") and UnitIsUnit('player', 'targettarget') and not (UnitClassification("target") == "worldboss") then CastSpellByName("Ghostly Strike()"); end
/script if UnitExists("target") and UnitIsUnit("targettarget", "player") and UnitClassification("target") == "worldboss" then CastSpellByName("Evasion"); end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Limited Invulnerability Potion")) and UnitExists("target") and UnitIsUnit("targettarget", "player") and UnitClassification("target") == "worldboss" and GetSpellCooldown(45, "spell") >0 and UnitHealth("player")/UnitHealthMax("player") <0.80 then UseContainerItem(b,s)SpellTargetUnit("player")end end end


/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"SliceDice")then f=1 s=GetPlayerBuffTimeLeft(b) end end end if s<10 and GetComboPoints("target")<5 then CastSpellByName("Sinister Strike()") end
/cast Sinister Strike

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Thistle Tea")) and BlF and UnitMana("Player")<=15 then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Juju Flurry")) and BlF  then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run if BlF then UseInventoryItem(13);UseInventoryItem(14);end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.50 and strfind(n,"Healthstone") then UseContainerItem(b,s)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.45 and  strfind(n,"Healing Potion")then UseContainerItem(b,s)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.40 and (strfind(n,"Nordanaar Herbal Tea") or strfind(n,"Tea with Sugar"))then UseContainerItem(b,s)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.35 and (strfind(n,"Whipper Root Tuber"))then UseContainerItem(b,s)end end end

```

## slice & dice
```


/script local found,duration=0,0 for i=0,31 do local b=GetPlayerBuff(i,"HELPFUL") if b>=0 then local t=GetPlayerBuffTexture(b) if t and string.find(t,"SliceDice") then found=1 duration=GetPlayerBuffTimeLeft(b) break end end end if (found==0 or (duration and duration<1.5)) and GetComboPoints()>0 and UnitAffectingCombat("player") then CastSpellByName("Slice and Dice") end


```
## Hemorrhage rotation

```
/run SnD=false for i=0,31,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run BlF=false for i=0,31,1 do gpb1=GetPlayerBuff(i,"HELPFUL"); if not (gpb1 == -1) and (strfind(GetPlayerBuffTexture(gpb1), "Ability_Warrior_PunishingBlow")) then BlF=true end end

/run if UnitHealth("target")==0 and UnitExists("target") then ClearTarget(); end
/run if GetUnitName("target")==nil then TargetNearestEnemy(); end

/run for z=1,172 do if IsAttackAction(z) then if not IsCurrentAction(z) then UseAction(z);end;end;end;

/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"SliceDice")then f=1 s=GetPlayerBuffTimeLeft(b) end end end if (f==0 or s<1) and GetComboPoints("target")>0  then CastSpellByName("Slice and Dice") end

/run if IsUsableAction(60) then CastSpellByName("Riposte()"); end

/run if (SnD and (IsUsableAction(60) and(UnitMana("Player")>=10))) then CastSpellByName("Surprise Attack()"); elseif SnD then CastSpellByName("Hemorrhage()"); else CastSpellByName("Slice and Dice()"); end


/script if UnitExists("target") and UnitIsUnit("targettarget", "player") and UnitClassification("target") == "worldboss" then CastSpellByName("Evasion"); end

/run if GetComboPoints("target")==0 then CastSpellByName("Hemorrhage()"); end
/run if UnitMana("Player")>=35 then CastSpellByName("Hemorrhage()"); end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Thistle Tea")) and BlF and UnitMana("Player")<=15 then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Juju Flurry")) and BlF  then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run if BlF then UseInventoryItem(13);UseInventoryItem(14);end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.50 and strfind(n,"Healthstone") then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.45 and  strfind(n,"Healing Potion")then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.40 and (strfind(n,"Nordanaar Herbal Tea") or strfind(n,"Tea with Sugar"))then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.35 and (strfind(n,"Whipper Root Tuber") )then UseContainerItem(b,s,1)end end end
```

## 战斗单刷
```
/run SnD=false for i=0,31,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run BlF=false for i=0,31,1 do gpb1=GetPlayerBuff(i,"HELPFUL"); if not (gpb1 == -1) and (strfind(GetPlayerBuffTexture(gpb1), "Ability_Warrior_PunishingBlow")) then BlF=true end end

/run if UnitHealth("target")==0 and UnitExists("target") then ClearTarget(); end
/run if GetUnitName("target")==nil then TargetNearestEnemy(); end

/run for z=1,172 do if IsAttackAction(z) then if not IsCurrentAction(z) then UseAction(z);end;end;end;

/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"SliceDice")then f=1 s=GetPlayerBuffTimeLeft(b) end end end if (f==0 or s<1) and GetComboPoints("target")>0  then CastSpellByName("Slice and Dice") end

/run if IsUsableAction(60) then CastSpellByName("Riposte()"); end

/run if IsUsableAction(59) then CastSpellByName("Surprise Attack()"); end

/run if (SnD and (IsUsableAction(60) and(UnitMana("Player")>=10))) then CastSpellByName("Surprise Attack()"); elseif SnD then CastSpellByName("Sinister Strike()"); else CastSpellByName("Slice and Dice()"); end


/script if UnitExists("target") and UnitIsUnit("targettarget", "player") and UnitClassification("target") == "worldboss" then CastSpellByName("Vanish"); end

/run if GetComboPoints("target")==0 then CastSpellByName("Sinister Strike()"); end
/run if UnitMana("Player")>=40 then CastSpellByName("Sinister Strike()"); end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Thistle Tea")) and BlF and UnitMana("Player")<=15 then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Juju Flurry")) and BlF  then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run if BlF then UseInventoryItem(13);UseInventoryItem(14);end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.50 and strfind(n,"Healthstone") then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.45 and  strfind(n,"Healing Potion")then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.40 and (strfind(n,"Nordanaar Herbal Tea") or strfind(n,"Tea with Sugar"))then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.35 and (strfind(n,"Whipper Root Tuber") )then UseContainerItem(b,s,1)end end end
```
## 血腥战斗
```
/run SnD=false for i=0,31,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run ToB=false for i=0,31,1 do db1=UnitBuff("player",i) if(db1~=nil and string.find(db1,"Bone")) then ToB=true end end
/run BlF=false for i=0,31,1 do gpb1=GetPlayerBuff(i,"HELPFUL"); if not (gpb1 == -1) and (strfind(GetPlayerBuffTexture(gpb1), "Ability_Warrior_PunishingBlow")) then BlF=true end end

/run if UnitHealth("target")==0 and UnitExists("target") then ClearTarget(); end
/run if GetUnitName("target")==nil then UnitXP("target", "nextEnemyConsideringDistance");end
/run if GetUnitName("target")==nil then TargetNearestEnemy(); end

/run for z=1,172 do if IsAttackAction(z) then if not IsCurrentAction(z) then UseAction(z);end;end;end;

/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"SliceDice")then f=1 s=GetPlayerBuffTimeLeft(b) end end end if (f==0 or s<1) and GetComboPoints("target")>0  then CastSpellByName("Slice and Dice") end

/run if not ToB  then  CastSpellByName("Rupture()"); end

/run if GetComboPoints("target")>4 and SnD and ToB then CastSpellByName("Eviscerate()"); end
/run if IsUsableAction(60) then CastSpellByName("Surprise Attack()"); end

/run if (ToB and SnD and (IsUsableAction(60) and(UnitMana("Player")>=10))) then CastSpellByName("Surprise Attack()"); elseif SnD and ToB then CastSpellByName("Sinister Strike()"); elseif not SnD then CastSpellByName("Slice and Dice()"); elseif not ToB then  CastSpellByName("Rupture()"); end
/script for i=0,31 do local b=GetPlayerBuff(i);if b>=0 then t=GetPlayerBuffTexture(b);if strfind(t,"SliceDice")then s=GetPlayerBuffTimeLeft(b);if s>1 and GetComboPoints("target")>3 and ToB then CastSpellByName("Eviscerate()");end;end;end;end


/run if UnitExists("target") and UnitIsUnit('player', 'targettarget') and not (UnitClassification("target") == "worldboss") then CastSpellByName("Ghostly Strike()"); end
/script if UnitExists("target") and UnitIsUnit("targettarget", "player") and UnitClassification("target") == "worldboss" then CastSpellByName("Evasion"); end

/run if GetComboPoints("target")==0 then CastSpellByName("Sinister Strike()"); end
/run if UnitMana("Player")>=40 then CastSpellByName("Sinister Strike()"); end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Thistle Tea")) and BlF and UnitMana("Player")<=15 then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Juju Flurry")) and BlF  then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run if BlF then UseInventoryItem(13);UseInventoryItem(14);end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.50 and strfind(n,"Healthstone") then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.45 and  strfind(n,"Healing Potion")then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.40 and (strfind(n,"Nordanaar Herbal Tea") or strfind(n,"Tea with Sugar"))then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.35 and (strfind(n,"Whipper Root Tuber") )then UseContainerItem(b,s,1)end end end
```
## 背刺小红龙

```
/run SnD=false for i=0,31,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run ToB=false for i=0,31,1 do db1=UnitBuff("player",i) if(db1~=nil and string.find(db1,"Bone")) then ToB=true end end
/run BlF=false for i=0,31,1 do gpb1=GetPlayerBuff(i,"HELPFUL"); if not (gpb1 == -1) and (strfind(GetPlayerBuffTexture(gpb1), "Ability_Warrior_PunishingBlow")) then BlF=true end end

/run if UnitHealth("target")==0 and UnitExists("target") then ClearTarget(); end
/run if GetUnitName("target")==nil then UnitXP("target", "nextEnemyConsideringDistance");end
/run if GetUnitName("target")==nil then TargetNearestEnemy(); end

/run for z=1,172 do if IsAttackAction(z) then if not IsCurrentAction(z) then UseAction(z);end;end;end;

/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"SliceDice")then f=1 s=GetPlayerBuffTimeLeft(b) end end end if (f==0 or s<2) and GetComboPoints("target")>4  then CastSpellByName("Slice and Dice") end

/run if not ToB & GetComboPoints("target")>4 then  CastSpellByName("Rupture()"); end

/run if GetComboPoints("target")>4 and SnD and ToB then CastSpellByName("Eviscerate()"); end
/run if IsUsableAction(60) then CastSpellByName("Surprise Attack()"); end

/script if UnitExists("target") and UnitIsUnit("targettarget", "player") and UnitClassification("target") == "worldboss" then CastSpellByName("Vanish"); end

/run if GetBonusBarOffset() == 1 then CastSpellByName("Ambush") elseif GetComboPoints()>4 then CastSpellByName("Eviscerate") else CastSpellByName("Backstab")end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Thistle Tea")) and BlF and UnitMana("Player")<=15 then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Juju Flurry")) and BlF  then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run if BlF then UseInventoryItem(13);UseInventoryItem(14);end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.50 and strfind(n,"Healthstone") then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.45 and  strfind(n,"Healing Potion")then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.40 and (strfind(n,"Nordanaar Herbal Tea") or strfind(n,"Tea with Sugar"))then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.35 and (strfind(n,"Whipper Root Tuber") )then UseContainerItem(b,s,1)end end end
```

## 取消无用buff

```
/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"Arcane Brilliance")then CancelPlayerBuff(b)  end end end
/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"Arcane Intellect")then CancelPlayerBuff(b)  end end end 
/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"Prayer of Spirit")then CancelPlayerBuff(b)  end end end
/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"Divine Spirit")then CancelPlayerBuff(b)  end end end
/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"Ancestral Fortitude")then CancelPlayerBuff(b)  end end end 

```
## 优化系统占用简单版
```

/run for z=13,24 do if IsAttackAction(z) then if not IsCurrentAction(z) then UseAction(z);end;end;end;
/script local f,s=0,0 for i=0,31 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"SliceDice")then f=1 s=GetPlayerBuffTimeLeft(b) end end end if (f==0 or s<1) and GetComboPoints("target")>0  then CastSpellByName("Slice and Dice") end
/run if GetComboPoints("target")>3 then CastSpellByName("Eviscerate()"); end
/cast Surprise Attack
/cast Sinister Strike

```
