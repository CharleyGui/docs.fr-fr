---
title: CustomDumpItem, structure
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616435"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem, structure
Décrit un élément à ajouter à un dump personnalisé dans le rapport d’erreurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`itemKind`|Valeur [ECustomDumpItemKind,](ecustomdumpitemkind-enumeration.md) qui indique le type d’élément à ajouter.|  
|`pReserved`|Pas utilisé pour l'instant. Tout élément ajouté à l’Union ne doit pas être supérieur à la taille du pointeur. Si un `struct` est requis, vous devez l’allouer séparément et pointer dessus.|  
  
## <a name="remarks"></a>Notes  
 [ICLRErrorReportingManager :: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) prend un paramètre de type `CustomDumpItem` .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d'hébergement](hosting-structures.md)
