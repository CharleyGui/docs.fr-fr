---
title: CLR_DEBUGGING_VERSION, structure
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 8a2abe847728a2bb1f1345ef73e55b58e4704001
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729809"
---
# <a name="clr_debugging_version-structure"></a>CLR_DEBUGGING_VERSION, structure

Définit la version du produit de CLR (Common Language Runtime) à des fins de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`wStructVersion`|Numéro de version de la structure|  
|`wMajor`|Numéro de version principale.|  
|`wMinor`|Numéro de version secondaire.|  
|`wBuild`|Numéro de build.|  
|`wRevision`|Numéro de révision.|  
  
## <a name="remarks"></a>Remarques  

 `CLR_DEBUGGING_VERSION`Toutefois, la structure est identique à la structure COR_VERSION, mais la `CLR_DEBUGGING_VERSION` structure fournit un champ de version de structure supplémentaire ( `wStructVersion` ). Actuellement, ce champ doit avoir la valeur zéro.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
