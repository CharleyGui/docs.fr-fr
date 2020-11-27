---
title: Événements de sécurité ETW
description: Comprendre les événements ETW de sécurité, qui sont déclenchés pendant la vérification de nom fort et la vérification Authenticode dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 4402bf5690a53ce518077268a3e20a95aeb14e8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272512"
---
# <a name="security-etw-events"></a>Événements de sécurité ETW

Les événements de sécurité sont déclenchés pendant la vérification de nom fort et la vérification Authenticode.  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1  

 Le tableau suivant montre les mots clés et les niveaux. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Début de la vérification de nom fort.|  
|`StrongNameVerificationStop_V1`|182|Fin de la vérification de nom fort.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|Indicateurs de vérification.|  
|ErrorCode|win:UInt32|Code d'erreur HResult.|  
|FullyQualifiedAssemblyName|win:UnicodeString|Nom d'assembly qualifié complet.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1  

 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Début de la vérification Authenticode.|  
|`AuthenticodeVerificationStop_V1`|184|Fin de la vérification Authenticode.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|Indicateurs de vérification.|  
|ErrorCode|win:UInt32|Code d'erreur HResult.|  
|ModulePath|win:UnicodeString|Chemin d’accès du module.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
