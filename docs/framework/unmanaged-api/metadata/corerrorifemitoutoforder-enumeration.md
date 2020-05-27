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
ms.openlocfilehash: fec049297bfa12d86cb2a7f7950e84ae540832b1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007429"
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
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
