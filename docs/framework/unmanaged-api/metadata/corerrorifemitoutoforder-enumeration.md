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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16f6d7bf6fa1730d50cfe81526817e492a453dad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781985"
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
|`MDErrorOutOfOrderNone`|Indique que le compilateur ne doit pas générer des messages d’erreur.|  
|`MDErrorOutOfOrderAll`|Indique que le compilateur doit générer un message d’erreur lorsqu’un champ de propriété, événement, méthode ou paramètre est émis de manière désordonnée.|  
|`MDMethodOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’une méthode est émise en désordre.|  
|`MDFieldOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’un champ est émis en désordre.|  
|`MDParamOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’un paramètre est émis de manière désordonnée.|  
|`MDPropertyOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’une propriété est émise en désordre.|  
|`MDEventOutOfOrder`|Indique que le compilateur doit générer un message d’erreur lorsqu’un événement est émis en désordre.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
