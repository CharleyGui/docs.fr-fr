---
title: COR_GC_REFERENCE, structure
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61a9cad9d0ce807d62c811e77402b8cc6d8c6905
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740691"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE, structure
Contient des informations sur un objet qui doit faire l'objet d'une récupération de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`domain`|Pointeur vers le domaine d’application à laquelle appartient l’objet ou un handle. Sa valeur peut être `null`.|  
|`location`|ICorDebugValue ou une interface ICorDebugReferenceValue qui correspond à l’objet d’être le garbage collector.|  
|`type`|Un [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valeur d’énumération qui indique la provenance de la racine. Pour plus d'informations, consultez la section Remarques.|  
|`extraData`|Données supplémentaires sur l’objet de garbage collection. Ces informations dépendent de la source de l’objet, comme indiqué par le `type` champ. Pour plus d'informations, consultez la section Remarques.|  
  
## <a name="remarks"></a>Notes  
 Le `type` champ est un [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valeur d’énumération qui indique la provenance de la référence. Un particulier `COR_GC_REFERENCE` valeur peut refléter un des types suivants d’objets gérés :  
  
- Objets à partir de toutes les piles gérées (`CorGCReferenceType.CorReferenceStack`). Cela inclut des références en direct dans le code managé, ainsi que les objets créés par le common language runtime.  
  
- Objets à partir de la table de handles (`CorGCReferenceType.CorHandle*`). Cela inclut des références fortes (`HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT`) et les variables statiques dans un module.  
  
- Objets à partir de la file d’attente du finaliseur (`CorGCReferenceType.CorReferenceFinalizer`). La file d’attente du finaliseur racines des objets jusqu'à ce que le finaliseur s’est exécutée.  
  
 Le `extraData` champ contient des données supplémentaires en fonction de la source (ou type) de la référence. Les valeurs possibles sont les suivantes :  
  
- `DependentSource`. Si le `type` est `CorGCREferenceType.CorHandleStrongDependent`, ce champ est l’objet qui, si elle est actif, de l’objet pour le garbage collector à racines `COR_GC_REFERENCE.Location`.  
  
- `RefCount`. Si le `type` est `CorGCREferenceType.CorHandleStrongRefCount`, ce champ est le nombre de références du handle.  
  
- `Size`. Si le `type` est `CorGCREferenceType.CorHandleStrongSizedByref`, ce champ est la dernière taille de l’arborescence de l’objet pour lequel le garbage collector calculé les racines de l’objet. Notez que ce calcul n’est pas nécessairement à jour.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
