---
title: StackOverflowInfo, structure
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: a8a57cfcaf36949d4d10c6ec267a5f55a2aee5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729926"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo, structure

Stocke le type de dépassement qui s’est produit et les informations sur l’exception levée en raison du dépassement de capacité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`soType`|Valeur de l’énumération [StackOverflowType,](stackoverflowtype-enumeration.md) qui spécifie le type de dépassement de capacité.|  
|`pExceptionInfo`|Pointeur vers un objet Win32 `EXCEPTION_POINTERS` , qui contient un enregistrement d’exception avec une description indépendante de l’ordinateur d’une exception et un enregistrement de contexte avec une description dépendante de l’ordinateur du contexte du processeur au moment de l’exception.|  
  
## <a name="remarks"></a>Remarques  

 Un `StackOverflowInfo` objet est passé à la méthode [IActionOnCLREvent :: OnEvent](iactiononclrevent-onevent-method.md) pour les `Event_StackOverflow` événements.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d'hébergement](hosting-structures.md)
