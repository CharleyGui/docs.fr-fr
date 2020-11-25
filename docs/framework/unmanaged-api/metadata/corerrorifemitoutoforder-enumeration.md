---
title: CorErrorIfEmitOutOfOrder, énumération
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: 1d1b0cbb8be33f285b63e7353da973455e0fd752
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718850"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder, énumération

Contient des valeurs d'indicateur qui précisent les conditions dans lesquelles un message d'erreur doit être généré quand les métadonnées sont émises de manière désordonnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|Indique le comportement par défaut, qui ne génère pas de messages d’erreur.|  
|`MDErrorOutOfOrderNone`|Indique que le compilateur ne doit pas générer de messages d’erreur.|  
|`MDErrorOutOfOrderAll`|Indique que le compilateur doit générer un message d’erreur lorsqu’un champ, une propriété, un événement, une méthode ou un paramètre est émis dans le désordre.|  
|`MDMethodOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’une méthode est émise dans le désordre.|  
|`MDFieldOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’un champ est émis dans le désordre.|  
|`MDParamOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’un paramètre est émis dans le désordre.|  
|`MDPropertyOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’une propriété est émise dans le désordre.|  
|`MDEventOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’un événement est émis dans le désordre.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
