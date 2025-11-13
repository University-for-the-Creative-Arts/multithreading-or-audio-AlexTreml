#  FMOD Audio Middleware 

** Build Files:**  
` – build `build.zip` .

---

## Overview

- Integrated **FMOD Studio middleware** into Unreal Engine.  
- Created and triggered a **3D Timeline Event** for a looping background music track.  
- Used a **parameter-driven automation system** for dynamic EQ changes.  
- Validated FMOD functionality in a **packaged Windows build**.

---

## Integration

1. Downloaded **FMOD Studio Suite** and **Unreal Integration Plugin** from the FMOD website.  
2. Placed the FMOD plugin in the project’s `Plugins` folder.  
3. Opened Unreal Engine and selected **Help → Validate FMOD** to confirm integration.  
4. Set the **FMOD Studio Project Path**.  
5. Built audio banks in FMOD Studio using **F7**.  
6. Verified successful connection in the **Unreal Output Log** showing the Master Bank loaded.

---

## Event Creation in FMOD Studio

1. Created a new **3D Timeline Event**.  
2. Imported a **racing track**.  
3. Added a parameter called **“Video”** with a range of `0–1`.  
4. Applied automation curves to the **mid** and **high EQ bands** using the “Video” parameter.  
5. Adjusted the **Spatialiser** settings for the event:
   - Increased **Min Extent** value to `360` to disable spatialisation and ensure even playback.  
   - Increased **Max Distance** value to `8600` to prevent distance attenuation fade-out.  
6. Tested automation by manually adjusting the parameter slider in FMOD Studio.  
7. Assigned the event to the **Master Bank** to enable Unreal Engine access.  
8. Rebuilt all banks to include the new event and automation data.

---

## Integration and Testing in Unreal Engine

1. Created a **Blueprint Actor** named `Audio_Test`.  
2. Added an **FMOD Audio Component** referencing the 3D Timeline Event.  
3. Added a **Timeline** node to control the “Video” parameter.  
4. Configured the Timeline to loop over **40 seconds**, animating values `0 → 1 → 0`.  
5. Linked the Timeline output to the FMOD component’s **Set Parameter** node.  
6. Placed the actor in the level and played the scene in the Unreal Editor.  
7. Confirmed:
   - The background track played correctly.  
   - EQ automation responded dynamically to the Timeline parameter.

---

## Validation in Packaged Build

1. Packaged the project as a **Windows (64-bit)** build.  
2. Verified **FMOD bank files** were included and functional in the packaged build.  
3. During packaging, the **Output Log** displayed multiple FMOD integration messages confirming successful inclusion, such as:

LogPluginManager: Mounting Project plugin FMODStudio

LogFMOD: FFMODStudioModule::LoadDll: Loading fmodstudioL.dll

LogFMOD: Path: Master.bank


These log entries verified that the **FMOD plugin**, **runtime libraries**, and **audio banks** were successfully compiled and loaded into the packaged executable.

---


