---
title: MALLOC_TYPE (énumération)
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
ms.openlocfilehash: fe58a519d0feac0da49e7778247da1ef538f8b83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730030"
---
# <a name="malloc_type-enumeration"></a>MALLOC_TYPE (énumération)

Contient des valeurs qui spécifient les caractéristiques de la mémoire qui est allouée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|La mémoire allouée peut contenir un fichier exécutable.|  
|`MALLOC_THREADSAFE`|La mémoire allouée est thread-safe. Autrement dit, la mémoire est accessible par plusieurs threads sans aucune synchronisation.<br /><br /> Si cet indicateur n’est pas défini, les appels sur l’objet doivent être sérialisés.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
