 
 ​local​ QBCore ​=​ exports[​'​qb-core​'​]:​GetCoreObject​() 
 ​local​ nativetheme ​=​ ​false​ ​--​ true for NativeUI theme 
 ​local​ vehiclemenu ​=​ nativetheme ​and​ MenuV:​CreateMenu​(​'​Vehicle Menu​'​, ​'​'​, ​'​topright​'​, ​220​, ​20​, ​60​, ​'​size-125​'​, ​'​default​'​, ​'​menuv​'​, ​'​vehiclemenu​'​, ​'​native​'​) ​or​ MenuV:​CreateMenu​(​false​, ​'​Vehicle Menu​'​, ​'​topright​'​, ​220​, ​20​, ​60​, ​'​size-125​'​, ​'​none​'​, ​'​menuv​'​, ​'​vehiclemenu​'​) 
 ​local​ liverymenu ​=​ nativetheme ​and​ MenuV:​CreateMenu​(​'​Livery Menu​'​, ​'​'​, ​'​topright​'​, ​220​, ​20​, ​60​, ​'​size-125​'​, ​'​default​'​, ​'​menuv​'​, ​'​liverymenu​'​, ​'​native​'​) ​or​ MenuV:​CreateMenu​(​false​, ​'​Livery Menu​'​, ​'​topright​'​, ​220​, ​20​, ​60​, ​'​size-125​'​, ​'​none​'​, ​'​menuv​'​, ​'​liverymenu​'​) 
 ​local​ extramenu ​=​ nativetheme ​and​ MenuV:​CreateMenu​(​'​Extra Menu​'​, ​'​'​, ​'​topright​'​, ​220​, ​20​, ​60​, ​'​size-125​'​, ​'​default​'​, ​'​menuv​'​, ​'​extramenu​'​, ​'​native​'​) ​or​ MenuV:​CreateMenu​(​false​, ​'​Extra Menu​'​, ​'​topright​'​, ​220​, ​20​, ​60​, ​'​size-125​'​, ​'​none​'​, ​'​menuv​'​, ​'​extramenu​'​) 
  
 ​RegisterCommand​(​'​vehiclemenu​'​, ​function​() 
 ​    ​local​ PlayerData ​=​ QBCore.​Functions​.​GetPlayerData​() 
 ​    ​local​ ped ​=​ ​PlayerPedId​() 
 ​    ​local​ veh ​=​ ​GetVehiclePedIsIn​(ped) 
 ​    ​if​ PlayerData.​job​.​name​ ​==​ ​'​police​'​ ​then 
 ​        ​if​ ​IsPedInAnyVehicle​(ped) ​and​ ​GetPedInVehicleSeat​(veh, ​-​1​) ​==​ ped ​then 
 ​            MenuV:​OpenMenu​(vehiclemenu) 
 ​        ​end 
 ​    ​end 
 ​end​) 
  
 ​RegisterKeyMapping​(​'​vehiclemenu​'​, ​'​Open Vehicle Menu​'​, ​'​keyboard​'​, ​'​F11​'​) 
  
 ​local​ livery_button ​=​ vehiclemenu:​AddButton​({ 
 ​    label ​=​ ​'​Livery Options​'​, 
 ​    value ​=​ liverymenu, 
 ​    description ​=​ ​'​Change Vehicle Livery​' 
 ​}) 
  
 ​livery_button:​On​(​'​select​'​, ​function​() 
 ​    liverymenu:​ClearItems​() 
 ​    ​local​ veh ​=​ ​GetVehiclePedIsIn​(​PlayerPedId​()) 
 ​    ​for​ liveryCount ​=​ ​1​, ​GetVehicleLiveryCount​(veh) ​do 
 ​        ​local​ livery ​=​ liverymenu:​AddButton​({ 
 ​            label ​=​ ​'​Livery #​'​ ​..​ liveryCount, 
 ​            description ​=​ ​'​Select Livery #​'​ ​..​ liveryCount, 
 ​            select ​=​ ​function​() 
 ​                ​SetVehicleLivery​(veh, liveryCount) 
 ​            ​end​}) 
 ​    ​end 
 ​end​) 
  
 ​local​ extra_button ​=​ vehiclemenu:​AddButton​({ 
 ​    label ​=​ ​'​Extra Options​'​, 
 ​    value ​=​ extramenu, 
 ​    description ​=​ ​'​Toggle Vehicle Extras​' 
 ​}) 
  
 ​extra_button:​On​(​'​select​'​, ​function​() 
 ​    extramenu:​ClearItems​() 
 ​    ​local​ veh ​=​ ​GetVehiclePedIsIn​(​PlayerPedId​()) 
 ​    ​for​ i ​=​ ​1​, ​12​ ​do 
 ​        ​if​ ​DoesExtraExist​(veh, i) ​then 
 ​            ​local​ isExtra ​=​ ​IsVehicleExtraTurnedOn​(veh, i) 
 ​            ​local​ extra ​=​ extramenu:​AddCheckbox​({ 
 ​                label ​=​ ​'​Extra #​'​ ​..​ i, 
 ​                value ​=​ isExtra, 
 ​                description ​=​ ​'​Toggle Extra #​'​ ​..​ i, 
 ​                change ​=​ ​function​() 
 ​                    ​TriggerEvent​(​'​mystic-vehiclemenu:client:extraToggle​'​, i) 
 ​                ​end​}) 
 ​        ​end 
 ​    ​end 
 ​end​) 
  
 ​local​ extraToggle ​=​ ​false 
 ​RegisterNetEvent​(​'​mystic-vehiclemenu:client:extraToggle​'​, ​function​(​i​) 
 ​    extraToggle ​=​ ​not​ extraToggle 
 ​    ​local​ veh ​=​ ​GetVehiclePedIsIn​(​PlayerPedId​()) 
 ​    ​SetVehicleExtra​(veh, i, extraToggle) 
 ​end​)
