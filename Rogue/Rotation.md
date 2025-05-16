## A simple Rotation
```
/run SnD=false for i=1,16,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run if GetComboPoints("target")==5 then CastSpellByName("Eviscerate()");elseif SnD then CastSpellByName("Sinister Strike()");elseif GetComboPoints("target")==0 then CastSpellByName("Sinister Strike()"); else CastSpellByName("Slice and Dice()"); end
```
it Checks if Slice and Dice is up, if not he casts slice and dice.
if the Target has 5 combo points and SnD is up, he uses eviscerate
only pressing one button, a simple beginning, but more is following !

This Rotation is meant for Pve Sword Rogues who got improved SnD
you als no need SuperMacro because it exceeds the 255 char limit


## Improved Rotation
```
/run RuP=false for r=1,16,1 do db=UnitDebuff("target",r) if(db~=nil and string.find(db,"Rupture")) then RuP=true end end
/run SnD=false for i=1,16,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run if GetComboPoints("target")==5 then CastSpellByName("Eviscerate()"); end
/run if GetComboPoints("target")==0 then CastSpellByName("Sinister Strike()"); end
/run if SnD then CastSpellByName("Sinister Strike()"); else CastSpellByName("Slice and Dice()"); end
/run if RuP then CastSpellByName("Sinister Strike()"); else CastSpellByName("Rupture()"); end
```
Almost the same as above, but in this case it Checks if you have SnD up, if you dont he recasts it, but also checks if you have Rupture on the Enemy if not he recasts it if he has the Combopoints for it. if Rupture and SnD are up and you reach 5 Cp he does Eviscerate.

This Rotation is meant for Pve Sword Rogues who got improved SnD
you als no need SuperMacro because it exceeds the 255 char limit

If you actually combine this macro with "IsUsableSpell" and insert a spellreaction like Bladefury or Adrenaline Rush, you would have a complete rotation where you dont have to watch for CD's or keeping up your at all. just concentrate on movement and do the best of dps while u move, BUT this is just a theory! (alot of things would still be missing like Autoattack for switching targets and a macro if the current target is not a Boss to use something else, in order to do also MAX dps @trash)


## Ambush, Coldblood & eviscerate
```
/run Stl=false for i=1,16 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"Stealth")) then Stl=true end end
/script if Stl then CastSpellByName("Ambush()"); elseif not Stl then CastSpellByName("Cold Blood()"); elseif GetComboPoints("target")<0 then CastSpellByName("Eviscerate()"); end
```
After using Ambush, instant pop Cold Blood and do eviscerate. Normaly i would like to add Trinkets like the AQ40 trashmob trinket or Ramsteins L Bolt trinket in order to make a oneshot macro, but since i dont have these items, it wont happen :3

-- Request from Confined :3 --


## Rotation to keep every debuff on the Enemy up
```
/run SnD=false for i=1,32,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run RuP=false for r=1,16,1 do ddb1=UnitDebuff("target",r) if(ddb1~=nil and string.find(ddb1,"Rupture")) then RuP=true end end
/run ExP=False for e=1,16,1 do ddb2=UnitDebuff("target",e) if(ddb2~=nil and string.find(ddb2,"Warrior_Riposte")) then ExP=true end end
/script AttackTarget();
/run if GetComboPoints("target")==0 then CastSpellByName("Sinister Strike()"); end
/run if SnD then CastSpellByName("Sinister Strike()"); else CastSpellByName("Slice and Dice()"); end
/run if ExP then CastSpellByName("Sinister Strike()"); else CastSpellByName("Expose Armor()"); end
/run if RuP then CastSpellByName("Sinister Strike()"); else CastSpellByName("Rupture()"); end
```
This Rotation is only desired to keep every debuff on the Enemy up, aswell SnD on yourself, the Priority is : "SnD > Expose Armor > Rupture" as Finisher.
Kinda Interessting Idea.

-- Request from LoGyMW --


## Rotation to refresh SliceDice if <1s.  5 CPs eveiscerate. 
## To Fit Turtle WOW, Superise Attack if possible. if 3+ CPs, and SliceDice >1, without SA, then eviscerate. If target's target is player, cast Ghostly Strike. If Blade Flurry, and energy low, use Tea, use Juju Flurry and trinket. Low health, use healthstone, tea with sugar, healing potion, whipper root tuber accordingly. 

```
/run SnD=false for i=1,32,1 do db=UnitBuff("player",i) if(db~=nil and string.find(db,"SliceDice")) then SnD=true end end
/run BlF=false for i=1,32,1 do gpb1=GetPlayerBuff(i,"HELPFUL"); if not (gpb1 == -1) and (strfind(GetPlayerBuffTexture(gpb1), "Ability_Warrior_PunishingBlow")) then BlF=true end end

/run if UnitHealth("target")==0 and UnitExists("target") then ClearTarget(); end
/run if GetUnitName("target")==nil then TargetNearestEnemy(); end

/run for z=1,172 do if IsAttackAction(z) then if not IsCurrentAction(z) then UseAction(z);end;end;end;

/script local f,s=0,0 for i=1,32 do b=GetPlayerBuff(i) if b>=0 then t=GetPlayerBuffTexture(b) if strfind(t,"SliceDice")then f=1 s=GetPlayerBuffTimeLeft(b) end end end if (f==0 or s<1) and GetComboPoints("target")>0  then CastSpellByName("Slice and Dice") end

/run if GetComboPoints("target")>4 and SnD then CastSpellByName("Eviscerate()"); end
/run if IsUsableAction(60) then CastSpellByName("Surprise Attack()"); end

/script for i=1,32 do local b=GetPlayerBuff(i);if b>=0 then t=GetPlayerBuffTexture(b);if strfind(t,"SliceDice")then s=GetPlayerBuffTimeLeft(b);if s>1 and GetComboPoints("target")>3 then CastSpellByName("Eviscerate()");end;end;end;end


/run if UnitIsUnit('player', 'targettarget') then CastSpellByName("Ghostly Strike()"); end
/script if UnitExists("target") and UnitIsUnit("targettarget", "player") and UnitClassification("target") == "worldboss" then CastSpellByName("Vanish") end

/run if GetComboPoints("target")==0 then CastSpellByName("Sinister Strike()"); end
/run if UnitMana("Player")>=40 then CastSpellByName("Sinister Strike()"); end

/run if (SnD and (IsUsableAction(60) and(UnitMana("Player")>=10))) then CastSpellByName("Surprise Attack()"); elseif SnD then CastSpellByName("Sinister Strike()"); else CastSpellByName("Slice and Dice()"); end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Thistle Tea")) and BlF and UnitMana("Player")<=15 then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and (strfind(n,"Juju Flurry")) and BlF  then UseContainerItem(b,s)SpellTargetUnit("player")end end end

/run if BlF then UseInventoryItem(13);UseInventoryItem(14);end

/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.50 and strfind(n,"Healthstone") then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.45 and (strfind(n,"Nordanaar Herbal Tea") or strfind(n,"Tea with Sugar"))then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.40 and  strfind(n,"Healing Potion")then UseContainerItem(b,s,1)end end end
/run for b=0,4 do for s=1,GetContainerNumSlots(b,s)do local n=GetContainerItemLink(b,s)if n and UnitHealth("player")/UnitHealthMax("player") <0.35 and (strfind(n,"Whipper Root Tuber") or strfind(n,"Night Dragon's Breath"))then UseContainerItem(b,s,1)end end end




```
