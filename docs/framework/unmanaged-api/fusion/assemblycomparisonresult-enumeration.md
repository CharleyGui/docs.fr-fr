---
title: AssemblyComparisonResult, énumération
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: cde25a9507006c89ef6490c13ae82033f04c2931
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731031"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult, énumération

Indique l’équivalence de deux identités d’assembly, telle que déterminée par la fonction [CompareAssemblyIdentity](compareassemblyidentity-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>Membres  
  
|Nom du membre|Description|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Indique que tous les champs d’assembly de la comparaison correspondent.|  
|`ACR_EquivalentFXUnified`|Indique que les assemblys sont considérés comme équivalents en fonction de l’unification de la version d’common language runtime (CLR) des numéros de version d’assembly dans la .NET Framework version 2,0.|  
|`ACR_EquivalentPartialFXUnified`|Indique une correspondance partielle des assemblys en fonction de l’unification CLR des numéros de version d’assembly dans le .NET Framework 2,0.|  
|`ACR_EquivalentPartialMatch`|Indique une correspondance partielle des assemblys.|  
|`ACR_EquivalentPartialUnified`|Indique une correspondance partielle des assemblys en fonction de l’unification héritée des numéros de version.|  
|`ACR_EquivalentPartialWeakNamed`|Indique une correspondance partielle d’assemblys simplement nommés.|  
|`ACR_EquivalentUnified`|Indique que les assemblys sont considérés comme équivalents en fonction de l’unification du CLR des numéros de version dans les versions héritées du .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Indique une correspondance entre deux assemblys simplement nommés dont les numéros de version ont été ignorés.|  
|`ACR_NonEquivalent`|Indique qu’aucune correspondance n’a été établie entre les deux assemblys.|  
|`ACR_NonEquivalentPartialVersion`|Indique que les deux assemblys correspondent, à l’exception de leurs numéros de version, qui correspondent uniquement partiellement.|  
|`ACR_NonEquivalentVersion`|Indique que les deux assemblys correspondent, à l’exception de leurs numéros de version, qui ne correspondent pas.|  
|`ACR_Unknown`|Indique que la raison d’une non-équivalence n’est pas connue.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CompareAssemblyIdentity, fonction](compareassemblyidentity-function.md)
- [Énumérations de fusion](fusion-enumerations.md)
