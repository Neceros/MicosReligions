# Mico's Religions
## Mod for Religions of Rimworld

Each religion can have a set of variables which indicate what a pawn must do, have, or be in order to join a religion. There’s a lot of stuff to cover. For a brief panic here’s an [example religion template](https://github.com/basarab1504/ReligionsOfRimworld-2.0/wiki/RELIGION-DEF-EXAMPLE). Just check it over and then come back here I’ll explain it.

### ReligionDef [The start]
```xml
<ReligionsOfRimworld.ReligionDef>
  <defName>MechaBretonHive</defName>
  <label>Mecha Breton Hive</label>
  <description>Transhumanists. Metalheads. This technologically minded religion worships the advnacement of humanity into the realms of technology and synthetic materials. The ultimate goal for each individual within the hive is to ascend into a pure robotic body.</description>
  <settingsDefs>
    <li>MBH_JoiningCriteriaSettings</li>
  </settingsDefs>
</ReligionsOfRimworld.ReligionDef>
```

You know how defs work. This stuff is probably self explainable. I've used Mecha Bretons are an example here, and this is all from my mind so obviously up for change.

You'll see under `settingsDefs` there can be a list of defs we can point to, which will be all of our special rules for this religion. Right now you see `MBH_JoiningCriteriaSettings` listed there. This is just telling Religions of Rimworld (RoR) that it should look for defNames with the listed names. 

Let's see what that looks like:
```xml
<ReligionsOfRimworld.ReligionSettingsDef ParentName="RoRJoiningCriteriaBase">
  <defName>MBH_JoiningCriteriaSettings</defName>
  <settings Class="ReligionsOfRimworld.ReligionSettings_JoiningCriteria">
    <criteria>
      <li Class="ReligionsOfRimworld.JoiningCriteria_Trait">
        <criteria>Transhumanist</criteria>
        <importance>Critical</importance>
        <shouldHave>true</shouldHave>
      </li>
      <li Class="ReligionsOfRimworld.JoiningCriteria_Hediff">
        <criteria>BionicEye</Criteria>
        <importance>Important</importance>
        <shouldHave>true</shouldHave>			
      </li>
      <li Class="ReligionsOfRimworld.JoiningCriteria_Gender">
        <criteria>Male</criteria>
        <importance>Low</importance>
        <shouldHave>true</shouldHave>
      </li>
    </criteria>
  </settings>
</ReligionsOfRimworld.ReligionSettingsDef>	
```

`shouldHave` is defaulted to true and can be omitted. `importance` can be Low, Standard, Important, and Critical. Low is default and can be omitted.

You can require pawns (your colonists and other generated pawns) have certain traits, hediffs, and or gender.
