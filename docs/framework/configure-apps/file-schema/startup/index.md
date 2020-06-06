---
title: Schéma des paramètres de démarrage
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701513"
---
# <a name="startup-settings-schema"></a>Schéma des paramètres de démarrage

Les paramètres de démarrage spécifient la version du common language runtime qui doit exécuter l’application.  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime. Les applications générées avec la version 1,1 du Runtime doivent utiliser l' **\<supportedRuntime>** élément.|  
|[\<supportedRuntime>](supportedruntime-element.md)|Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.|  
|[\<startup>](startup-element.md)|Contient les **\<requiredRuntime>** **\<supportedRuntime>** éléments et.|  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des fichiers de configuration](../index.md)
- [Comment : configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
