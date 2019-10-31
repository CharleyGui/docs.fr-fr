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
ms.openlocfilehash: 635cb0c003889beb2f78e8413189cbfc4b064175
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099144"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE, structure
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
|`domain`|Pointeur vers le domaine d’application auquel le handle ou l’objet appartient. Sa valeur peut être `null`.|  
|`location`|Une interface ICorDebugValue ou ICorDebugReferenceValue qui correspond à l’objet devant faire l’objet d’un garbage collection.|  
|`type`|Valeur d’énumération [corgcreferencetype,](corgcreferencetype-enumeration.md) qui indique où provient la racine. Pour plus d'informations, consultez la section Remarques.|  
|`extraData`|Données supplémentaires sur l’objet qui doit être récupéré par le garbage collector. Ces informations dépendent de la source de l’objet, comme indiqué dans le champ `type`. Pour plus d'informations, consultez la section Remarques.|  
  
## <a name="remarks"></a>Notes  
 Le champ `type` est une valeur d’énumération [corgcreferencetype,](corgcreferencetype-enumeration.md) qui indique l’origine de la référence. Une valeur de `COR_GC_REFERENCE` particulière peut refléter l’un des types d’objets managés suivants :  
  
- Objets de toutes les piles managées (`CorGCReferenceType.CorReferenceStack`). Cela comprend les références dynamiques en code managé, ainsi que les objets créés par l’common language runtime.  
  
- Objets de la table de handles (`CorGCReferenceType.CorHandle*`). Cela comprend des références fortes (`HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT`) et des variables statiques dans un module.  
  
- Objets de la file d’attente du finaliseur (`CorGCReferenceType.CorReferenceFinalizer`). Le finaliseur met les objets racine en file d’attente jusqu’à l’exécution du finaliseur.  
  
 Le champ `extraData` contient des données supplémentaires en fonction de la source (ou du type) de la référence. Les valeurs possibles sont :  
  
- `DependentSource`., Si le `type` est `CorGCREferenceType.CorHandleStrongDependent`, ce champ est l’objet qui, s’il est actif, racine l’objet qui doit être récupéré par le garbage collector au `COR_GC_REFERENCE.Location`.  
  
- `RefCount`., Si le `type` est `CorGCREferenceType.CorHandleStrongRefCount`, ce champ correspond au décompte de références du descripteur.  
  
- `Size`., Si le `type` est `CorGCREferenceType.CorHandleStrongSizedByref`, ce champ est la dernière taille de l’arborescence d’objets pour laquelle le garbage collector a calculé les racines de l’objet. Notez que ce calcul n’est pas nécessairement à jour.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
