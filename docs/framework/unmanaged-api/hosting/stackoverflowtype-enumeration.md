---
title: StackOverflowType, énumération
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: f399d33dbe05cb5768aa45533ef30d28409e18e2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006465"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType, énumération
Contient des valeurs qui indiquent la cause sous-jacente d’un événement de dépassement de capacité de la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`SO_ClrEngine`|Le dépassement de capacité de la pile a été provoqué par le moteur d’exécution.|  
|`SO_Managed`|Le dépassement de capacité de la pile a été provoqué par du code managé.|  
|`SO_Other`|Le dépassement de capacité de la pile a été provoqué par du code non managé.|  
  
## <a name="remarks"></a>Remarques  
 Ces informations sont passées à l’hôte via un appel à la méthode [IActionOnCLREvent :: OnEvent](iactiononclrevent-onevent-method.md) .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
