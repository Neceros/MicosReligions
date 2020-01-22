# Mico's Religions
## Mod for Religions of Rimworld


#### Designed for Mico's Twitch Stream: [Check out Mico's twitch](https://www.twitch.tv/Micoinkwell)

Each religion can have a set of variables which indicate what a pawn must do, have, or be in order to join a religion. There’s a lot of stuff to cover. 

For a brief panic here’s the [full religion example](https://github.com/Neceros/MicosReligions/blob/master/Defs/ReligionDefs/MechaBretons.xml). Just check it over and then come back here and relax, because I’ll explain it.

### The Core
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


### Joining Criteria
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



### Killing Settings
```xml
<ReligionsOfRimworld.ReligionSettingsDef ParentName="RoRKillSettingsBase">
  <defName>MBH_KillSettings</defName>
  <settings Class="ReligionsOfRimworld.ReligionSettings_Social">	
  <properties>
    <li Class="ReligionsOfRimworld.ReligionProperty_ThingDef">
      <propertyObject>Human</propertyObject>
      <pawnCategory>Hostile</pawnCategory>
      <subject>
        <piety>RoR_PietyKillGood</piety>
      </subject>
    </li>
    <li Class="ReligionsOfRimworld.ReligionProperty_ThingDef">
      <propertyObject>Mech_Centipede</propertyObject>
      <subject>
        <thought>RoR_ThoughtKillBad</thought>
      </subject>
    </li>
    <li Class="ReligionsOfRimworld.ReligionProperty_ThingDef">
      <propertyObject>Mech_Lancer</propertyObject>
      <subject>
        <thought>RoR_ThoughtKillBad</thought>
      </subject>
    </li>
    <li Class="ReligionsOfRimworld.ReligionProperty_ThingDef">
      <propertyObject>Mech_Scyther</propertyObject>
      <subject>
        <thought>RoR_ThoughtKillBad</thought>
      </subject>
    </li>
  </properties>		
  </settings>
</ReligionsOfRimworld.ReligionSettingsDef>
```

So, this is saying mecha bretons get good piety when they kill enemies (they are pleasing their god.) Also, if you kill any of the mechs you get a bad opinion about it. Your god understands, you don't lose piety, but you feel bad about doing it.

#### Avaliable defs
<dl>
  <dt>Thought</dt>
  <dd>RoR_ThoughtKillBad</dd>
  <dd>RoR_ThoughtKillGood</dd>

  <dt>Piety</dt>
  <dd>RoR_PietyKillBad</dd>
  <dd>RoR_PietyKillGood</dd>
</dl>



### Weapon Settings
```xml
<ReligionsOfRimworld.ReligionSettingsDef ParentName="RoRWeaponSettingsBase">
  <defName>MBH_WeaponSettings</defName>
  <settings Class="ReligionsOfRimworld.ReligionSettings_Social">	
  <properties>
    <li Class="ReligionsOfRimworld.ReligionProperty_ThingDef">
      <propertyObject>Gun_ChargeRifle</propertyObject>
      <subject>
        <piety>RoR_PietyWeaponKillGood</piety>
        <thought>RoR_ThoughtWeaponKillGood</thought>
      </subject>	
    </li>		
  </properties>		
  </settings>
</ReligionsOfRimworld.ReligionSettingsDef>
```

This is pretty straight forward. You get piety or opinion changes base on doing stuff with specified weapons.

#### Avaliable defs
<dl>
  <dt>Thought</dt>
  <dd>RoR_ThoughtWeaponKillBad</dd>
  <dd>RoR_ThoughtWeaponKillGood</dd>

  <dt>Piety</dt>
  <dd>RoR_PietyWeaponKillBad</dd>
  <dd>RoR_PietyWeaponKillGood</dd>
</dl>



### Food Settings
```xml
<ReligionsOfRimworld.ReligionSettingsDef ParentName="RoRFoodSettingsBase">
  <defName>MBH_FoodSettings</defName>
  <settings Class="ReligionsOfRimworld.ReligionSettings_Social">	
  <properties>
    <li Class="ReligionsOfRimworld.ReligionProperty_ThingDef">
      <propertyObject>Corpse_YorkshireTerrier</propertyObject>
      <subject>
        <piety>RoR_PietyFoodBad</piety>
      </subject>
    </li>
    <li Class="ReligionsOfRimworld.ReligionProperty_ThingDef">
      <propertyObject>Meat_YorkshireTerrier</propertyObject>
      <subject>
        <piety>RoR_PietyFoodBad</piety>
      </subject>
    </li>
  </properties>		
  </settings>
</ReligionsOfRimworld.ReligionSettingsDef>
```

This is pretty straight forward. You get piety or opinion changes based on eating something.

#### Avaliable defs
<dl>
  <dt>Thought</dt>
  <dd>RoR_ThoughtFoodBad</dd>
  <dd>RoR_ThoughtFoodGood</dd>

  <dt>Piety</dt>
  <dd>RoR_PietyFoodBad</dd>
  <dd>RoR_PietyFoodGood</dd>
</dl>



### Opinion Settings
```xml
<ReligionsOfRimworld.ReligionSettingsDef ParentName="RoROpinionSettingsBase">
  <defName>MBH_OpinionSettings</defName>
  <settings Class="ReligionsOfRimworld.ReligionSettings_Social">	
  <defaultProperty>
    <witness>
      <opinionThought>RoR_ThoughtOpinionBad</opinionThought>
    </witness>			
  </defaultProperty>
  <properties>
    <li Class="ReligionsOfRimworld.ReligionProperty_ReligionDef">
      <propertyObject>ChurchofHONK</propertyObject>
      <witness>
        <opinionThought>RoR_ThoughtOpinionBad</opinionThought>
      </witness>	
    </li>
    <li Class="ReligionsOfRimworld.ReligionProperty_ReligionDef">
      <propertyObject>GoatboySociety</propertyObject>
      <witness>
        <opinionThought>RoR_ThoughtOpinionGood</opinionThought>
      </witness>	
    </li>
  </properties>		
  </settings>
</ReligionsOfRimworld.ReligionSettingsDef>
```

Pawns have an opinion about each other depending on their deeds, bloodlines, and more. Religion can be an extra reason for your pawn to make on opinion about someone else. Pawns can like or dislike someone based on religion.

Mecha bretons would dislike looking at a honker, but a good opnion of goatboys. If you specify a `defaultProperty`, you can omit the witness opinion in a `ReligionProperty_ReligionDef`listing.

#### Avaliable defs
<dl>
  <dt>OpinionThought</dt>
  <dd>RoR_ThoughtOpinionBad</dd>
  <dd>RoR_ThoughtOpinionGood</dd>
</dl>



### Apparel Settings
```xml
<ReligionsOfRimworld.ReligionSettingsDef ParentName="RoRApparelSettingsBase">
  <defName>MBH_ApparelSettings</defName>
  <settings Class="ReligionsOfRimworld.ReligionSettings_Social">	
  <properties>
    <li Class="ReligionsOfRimworld.ReligionProperty_ThingDef">
      <propertyObject>Plasteel</propertyObject>
      <subject>
        <piety>RoR_PietyApparelStuffGood</piety>
      </subject>
    </li>
  </properties>		
  </settings>
</ReligionsOfRimworld.ReligionSettingsDef>
```

Define apparel you want to affect your pawn. The amount of clothes on the pawn multiplies the effect. 

As far as I can tell the above xml will give your pawn good piety when wearing anything made of plasteel. I still don't know a whole lot about this section. Will update later.

#### Avaliable defs
<dl>
  <dt>Thought</dt>
  <dd>RoR_ThoughtApparelBad</dd>
  <dd>RoR_ThoughtApparelGood</dd>
  <dd>RoR_ThoughtApparelStuffBad</dd>
  <dd>RoR_ThoughtApparelStuffGood</dd>
  
  <dt>Piety</dt>
  <dd>RoR_PietyApparelBad</dd>
  <dd>RoR_PietyApparelGood</dd>
  <dd>RoR_PietyApparelStuffBad</dd>
  <dd>RoR_PietyApparelStuffGood</dd>
</dl>



### Worship Settings
```xml
<ReligionsOfRimworld.ReligionSettingsDef ParentName="RoRWorshipSettingsBase">
  <defName>MBH_WorshipSettings</defName>
  <settings Class="ReligionsOfRimworld.ReligionSettings_ReligionActivity">	
    <properties>
      <li Class="ReligionsOfRimworld.ReligionProperty_ActivityTaskDef">
        <propertyObject>RoR_TaskWorship</propertyObject>
        <subject>
          <piety>RoR_PietyWorshipAverage</piety>
        </subject>
        <witness>
          <piety>RoR_PietyWorshipSmall</piety>
        </witness>
      </li>	
    </properties>
  </settings>
</ReligionsOfRimworld.ReligionSettingsDef>
```

Honestly I don't know what this does. All the religions are like this so... I just copied them. There doesn't seem to be any documentation on it.



### Buildings Settings
```xml
<ReligionsOfRimworld.ReligionSettingsDef ParentName="RoRAllowedBuildingsSettingsBase">
  <defName>MC_AllowedBuildingsSettings</defName>
  <settings Class="ReligionsOfRimworld.ReligionSettings_AllowedBuildings">	
  <allowedBuildings>
    <li>AltarWithBook</li>
    <li>WorshipSpot</li>
    <li>FabricationBench</li>
  </allowedBuildings>	
  </settings>
</ReligionsOfRimworld.ReligionSettingsDef>
```

Religious pawns need to pray and worship at specified buildings, in order to gain piety, good thoughts, and stuff.

Just list the building defNames, like above.
