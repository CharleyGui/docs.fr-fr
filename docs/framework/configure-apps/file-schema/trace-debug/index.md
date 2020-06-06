---
title: Schéma des paramètres de traçage et de débogage
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
ms.openlocfilehash: 037d08b33e9aa6a64d236b36ebcf821b604b03df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927118"
---
# <a name="trace-and-debug-settings-schema"></a>Schéma des paramètres de traçage et de débogage
Les paramètres de traçage et débogage spécifient les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.  
  
 Le tableau suivant décrit la fonction de chaque élément des paramètres de traçage et de débogage.  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|Ajoute un écouteur à la collection `Listeners` pour une source de trace.|  
|[\<add>](add-element-for-listeners-for-trace.md)|Ajoute un écouteur à la collection `Listeners`.|  
|[\<add>](add-element-for-sharedlisteners.md)|Ajoute un écouteur à la collection `sharedListeners`.|  
|[\<add>](add-element-for-switches.md)|Spécifie le niveau auquel un commutateur de trace est défini.|  
|[\<assert>](assert-element.md)|Indique si une boîte de message doit s’afficher quand vous appelez la méthode <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; spécifie également le nom du fichier dans lequel écrire les messages.|  
|[\<clear>](clear-element-for-listeners-for-source.md)|Efface la collection `Listeners` pour une source de trace.|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|Efface la collection `Listeners` de la trace.|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|Ajoute un filtre à un écouteur dans la collection `Listeners` pour une trace.|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|Ajoute un filtre à un écouteur dans la collection `sharedListeners`.|  
|[\<listeners>](listeners-element-for-source.md)|Spécifie des écouteurs pour la collection `Listeners` pour une source de trace.|  
|[\<listeners>](listeners-element-for-trace.md)|Spécifie des écouteurs pour la collection `Listeners` pour une trace.|  
|[\<performanceCounters>](performancecounters-element.md)|Spécifie la taille de la mémoire globale partagée par les compteurs de performances.|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|Supprime un écouteur de la collection `Listeners` pour la trace.|  
|[\<remove>](remove-element-for-listeners-for-source.md)|Supprime un écouteur de la collection `Listeners` pour une source de trace.|  
|[\<sharedListeners>](sharedlisteners-element.md)|Contient des écouteurs auxquels toute source ou tout élément de trace peuvent faire référence.|  
|[\<sources>](sources-element.md)|Contient les sources de trace qui lancent des messages de traçage.|  
|[\<source>](source-element.md)|Spécifie une source de trace qui lance des messages de traçage.|  
|[\<switches>](switches-element.md)|Contient des commutateurs de traçage et le niveau auquel ils sont définis.|  
|[\<system.diagnostics>](system-diagnostics-element.md)|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|[\<trace>](trace-element.md)|Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [Schéma du fichier de configuration](../index.md)
