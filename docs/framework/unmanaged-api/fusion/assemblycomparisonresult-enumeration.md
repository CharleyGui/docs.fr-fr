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
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178288"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult, énumération
Indique l’équivalence de deux identités d’assemblage, déterminée par la fonction [CompareAssemblyIdentity.](compareassemblyidentity-function.md)  
  
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
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Indique que tous les champs d’assemblage dans la correspondance de comparaison.|  
|`ACR_EquivalentFXUnified`|Indique que les assemblages sont considérés comme équivalents en fonction de l’unification de la version en cours d’exécution (CLR) des numéros de version d’assemblage dans la version cadre .NET 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Indique une correspondance partielle des assemblées basée sur l’unification CLR des numéros de version d’assemblage dans le cadre .NET 2.0.|  
|`ACR_EquivalentPartialMatch`|Indique une correspondance partielle des assemblées.|  
|`ACR_EquivalentPartialUnified`|Indique une correspondance partielle des assemblages basée sur l’unification héritée des nombres de versions.|  
|`ACR_EquivalentPartialWeakNamed`|Indique une correspondance partielle d’assemblages simplement nommés.|  
|`ACR_EquivalentUnified`|Indique que les assemblages sont considérés comme équivalents en fonction de l’unification CLR des numéros de version dans les versions héritées du cadre .NET.|  
|`ACR_EquivalentWeakNamed`|Indique une correspondance entre deux assemblées simplement nommées dont les numéros de version ont été ignorés.|  
|`ACR_NonEquivalent`|Indique qu’aucun match n’a eu lieu entre les deux assemblées.|  
|`ACR_NonEquivalentPartialVersion`|Indique que les deux assemblages correspondent à l’exception de leurs numéros de version, qui ne correspondent que partiellement.|  
|`ACR_NonEquivalentVersion`|Indique que les deux assemblages correspondent à l’exception de leurs numéros de version, qui ne correspondent pas.|  
|`ACR_Unknown`|Indique que la raison de la non-équivalence n’est pas connue.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** Fusion.h  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CompareAssemblyIdentity, fonction](compareassemblyidentity-function.md)
- [Énumérations de fusion](fusion-enumerations.md)
