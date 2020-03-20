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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179316"
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
|`domain`|Un pointeur vers le domaine d’application auquel appartient la poignée ou l’objet. Sa valeur `null`peut être .|  
|`location`|Soit une ICorDebugValue, soit une interface ICorDebugReferenceValue qui correspond à l’objet à collecter.|  
|`type`|Une valeur d’énumération [CorGCReferenceType](corgcreferencetype-enumeration.md) qui indique d’où vient la racine. Pour plus d'informations, consultez la section Notes.|  
|`extraData`|Des données supplémentaires sur l’objet à collecter. Ces informations dépendent de la source de `type` l’objet, comme indiqué par le champ. Pour plus d'informations, consultez la section Notes.|  
  
## <a name="remarks"></a>Notes   
 Le `type` champ est une valeur de recensement [CorGCReferenceType](corgcreferencetype-enumeration.md) qui indique d’où vient la référence. Une `COR_GC_REFERENCE` valeur particulière peut refléter n’importe lequel des types suivants d’objets gérés :  
  
- Objets de toutes les`CorGCReferenceType.CorReferenceStack`piles gérées ( ). Cela inclut les références en direct dans le code géré, ainsi que les objets créés par l’heure d’exécution de la langue commune.  
  
- Objets de la`CorGCReferenceType.CorHandle*`table de poignée ( ). Cela comprend des`HNDTYPE_STRONG` `HNDTYPE_REFCOUNT`références fortes ( et ) et des variables statiques dans un module.  
  
- Objets de la file`CorGCReferenceType.CorReferenceFinalizer`d’attente finalisateur ( ). La file d’attente de finalisation racines objets jusqu’à ce que le finalizer a couru.  
  
 Le `extraData` champ contient des données supplémentaires en fonction de la source (ou du type) de la référence. Les valeurs possibles sont les suivantes :  
  
- `DependentSource`. Si `type` l’est `CorGCREferenceType.CorHandleStrongDependent`, ce champ est l’objet qui, si `COR_GC_REFERENCE.Location`vivant, racines de l’objet à collecter à la poubelle à .  
  
- `RefCount`. Si `type` le `CorGCREferenceType.CorHandleStrongRefCount`est , ce champ est le nombre de références de la poignée.  
  
- `Size`. Si `type` c’est `CorGCREferenceType.CorHandleStrongSizedByref`le cas, ce champ est la dernière taille de l’arbre objet pour lequel le éboueur a calculé les racines de l’objet. Notez que ce calcul n’est pas nécessairement à jour.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
