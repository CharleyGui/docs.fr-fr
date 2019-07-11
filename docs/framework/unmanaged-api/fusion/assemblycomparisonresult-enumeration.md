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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6c417eec9583ff069c9d61fa31e9c14f3931130
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778511"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult, énumération
Indique l’équivalence de deux identités d’assembly, tel que déterminé par le [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) (fonction).  
  
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
|`ACR_EquivalentFullMatch`|Indique qu’assembly tous les champs dans la correspondance de comparaison.|  
|`ACR_EquivalentFXUnified`|Indique que les assemblys sont considérées comme équivalentes en fonction de l’unification de version (CLR) common language runtime des numéros de version d’assembly dans le .NET Framework version 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Indique une correspondance partielle des assemblys selon l’unification CLR des numéros de version d’assembly dans le .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Indique une correspondance partielle des assemblys.|  
|`ACR_EquivalentPartialUnified`|Indique une correspondance partielle des assemblys selon l’unification héritée des numéros de version.|  
|`ACR_EquivalentPartialWeakNamed`|Indique une correspondance partielle des assemblys nommés simplement.|  
|`ACR_EquivalentUnified`|Indique que les assemblys sont considérées comme équivalentes en fonction de l’unification des numéros de version dans les versions héritées du .NET Framework CLR.|  
|`ACR_EquivalentWeakNamed`|Indique une correspondance entre deux assemblys simplement nommés dont les numéros de version ont été ignorés.|  
|`ACR_NonEquivalent`|Indique qu’aucune correspondance s’est produite entre les deux assemblys.|  
|`ACR_NonEquivalentPartialVersion`|Indique que les deux assemblys correspondent à l’exception de leurs numéros de version correspondent uniquement partiellement.|  
|`ACR_NonEquivalentVersion`|Indique que les deux assemblys correspondent à l’exception de leurs numéros de version qui ne correspondent pas.|  
|`ACR_Unknown`|Indique que la raison de non-équivalence n’est pas connue.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CompareAssemblyIdentity, fonction](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [Énumérations de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
