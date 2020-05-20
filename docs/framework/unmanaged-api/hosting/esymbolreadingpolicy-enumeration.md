---
title: ESymbolReadingPolicy, énumération
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 5c3d1d0ebc56ee93c950afb4f015c8e10ec6a0f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616175"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy, énumération
Contient des valeurs qui définissent la stratégie de lecture des fichiers de base de données du programme (PDB).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Spécifie que le débogueur doit toujours lire les fichiers PDB.|  
|`eSymbolReadingFullTrustOnly`|Spécifie que le débogueur doit lire uniquement les fichiers PDB associés à des assemblys de confiance totale.|  
|`eSymbolReadingNever`|Spécifie que le débogueur ne doit jamais lire les fichiers PDB.|  
  
## <a name="remarks"></a>Notes  
 L' `ESymbolReadingPolicy` énumération est utilisée avec la méthode [ICLRDebugManager :: SetSymbolReadingPolicy (](iclrdebugmanager-setsymbolreadingpolicy-method.md) .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
