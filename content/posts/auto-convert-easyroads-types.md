---
title: "Auto Convert Roads Types from Real World Terrain"
date: 2020-07-10T08:58:27+01:00
draft: false
---

Real World Terrain is a great Unity Asset to kick start a Unity Terrain based upon a real life location. 
One of the helpful features is that it will can also be used in conjunction with EasyRoads3D to generate a road network based on actual road data. 
However, you might find yourself in a situation were you've requested that all roads types (highways to dirt paths) are included but you end up with everything looking like 6 metre asphalt roads. 
If you're in this situation then you can use the following script (or tweaked to your needs) to convert them to something more useful. 
**NB It also sets the width of the road to that specified in the meta data.**

<!--more-->
Instructions:


  1.  Make sure you have a road type you want to use in EasyRoads3D, e.g. Track
  1.  Add the script to your 'Road Objects' game object
  1.  Set the 'Not From Road Surface' to surface that you DO NOT want to be effected by the change, e.g. asphalt, i.e. please don't change anything that has a surface of asphalt
  1.  Set the 'To Road Type' to the name of EasyRoads3D type your want, e.g. Track
  1.  Check the 'Should Run' field
  ```csharp
  using System;
using System.Linq;
using EasyRoads3Dv3;
using InfinityCode.RealWorldTerrain.OSM;
using UnityEngine;
 
namespace CBC
{
    [ExecuteInEditMode]
    public class EasyRoads3DTypeMapper : MonoBehaviour
    {
        [SerializeField]
        string fromNotRoadSurface;
         
        [SerializeField]
        string toRoadType;
 
        [SerializeField]
        bool shouldRun = false;
 
        private void OnValidate()
        {
            if (shouldRun)
            {
                int roadsChanged = 0;
                try
                {
                    var roadNetwork = new ERRoadNetwork();
                    if (roadNetwork == null)
                    {
                        Debug.LogError("Unknown road network");
                        shouldRun = false;
                        return;
                    }
 
                    var erModularBase = GetComponentInParent();
                    var roadTypes = erModularBase.GetRoadTypes();
                    // DisplayRoadTypes(roadTypes);
 
                    var requestedRoadType = roadTypes.FirstOrDefault(rt => rt.roadTypeName.Equals(toRoadType, System.StringComparison.InvariantCultureIgnoreCase));
                    if (requestedRoadType == null)
                    {
                        Debug.LogError("Unknown road type " + toRoadType);
                        shouldRun = false;
                        return;
                    }
 
                    var realWorldTerrainOSMMetas = GetComponentsInChildren();
                    foreach (var rwtRoad in realWorldTerrainOSMMetas)
                    {
                        var erRoad = rwtRoad.GetComponent();
                        RealWorldTerrainOSMMetaTag surface = GetMetaInfo(rwtRoad, "surface");
 
                        var isTargetSurfaceForChange = surface == null || (surface != null && !surface.info.Equals(fromNotRoadSurface, System.StringComparison.InvariantCultureIgnoreCase));
 
                        var roadType = erRoad.GetRoadType(roadTypes);
                        if (isTargetSurfaceForChange && roadType != requestedRoadType)
                        {
                            var estWidthInfo = GetMetaInfo(rwtRoad, "est_width");
                            var estWidth = estWidthInfo?.info ?? "0";
                            var requestedWidth = (float)Convert.ToDouble(estWidth);
 
                            print(roadType?.roadTypeName ?? "No road type set");
                            print($"{surface?.info ?? "(surface not set)"} != {fromNotRoadSurface}");
 
 
 
                            print($"Changing {erRoad.name} {roadType?.roadTypeName ?? "not set"} to {requestedRoadType.roadTypeName}");
                            print($"Current width: {erRoad.GetRoadWidth()} Requested Width {estWidth} ");
 
                            var road = erRoad.road;
                            if (road == null)
                            {
                                road = roadNetwork.GetRoadByName(erRoad.name);
                                if (road == null)
                                {
                                    Debug.LogError("Road name not found in network");
                                }
                            }
 
                            if (road == null)
                            {
                                Debug.LogError("Road is missing, cannot change any details");
                            }
                            else
                            {
                                road.SetRoadType(requestedRoadType);
                                if (requestedWidth > 0f)
                                {
                                    road.SetWidth(requestedWidth);
                                }
                                roadsChanged++;
                            }
                        }
                    }
                }
                finally
                {
                    print($"Changed {roadsChanged} roads in this run");
                    shouldRun = false;
                }
            }
        }
 
        private void DisplayRoadTypes(ERRoadType[] roadTypes)
        {
            for (int x = 0; x  m.title == key);
        }
 
        private static void DisplayMetaInfo(RealWorldTerrainOSMMeta rwtRoad)
        {
            print($"metaInfo: {rwtRoad.metaInfo.Length}");
            for (int x = 0; x < rwtRoad.metaInfo.Length; x++)
            {
                print($"{rwtRoad.metaInfo[x].title} {rwtRoad.metaInfo[x].info}");
            }
        }
    }
}
  ```


