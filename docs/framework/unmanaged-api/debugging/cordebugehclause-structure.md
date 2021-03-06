---
title: CorDebugEHClause, structure
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
ms.openlocfilehash: 225523280a2e1e0d8f51321e9dd865d901e725ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712701"
---
# <a name="cordebugehclause-structure"></a>CorDebugEHClause, structure

[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Représente une clause de gestion des exceptions pour un bloc spécifié de code de langage intermédiaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`Flags`|Un champ de bits qui décrit les informations de l'exception dans la clause de gestion des exceptions. Pour plus d'informations, consultez la section Remarques.|  
|`TryOffset`|Le décalage en octets du bloc `try` à partir du début du corps de la méthode.|  
|`TryLength`|La longueur en octets du bloc `try`.|  
|`HandlerOffset`|L'emplacement du gestionnaire pour ce bloc `try`.|  
|`HandlerLength`|La taille du code du gestionnaire en octets.|  
|`ClassToken`|Le jeton de métadonnées pour un gestionnaire d'exceptions basé sur les types.|  
|`FilterOffset`|Le décalage en octets depuis le début du corps de la méthode pour un gestionnaire d'exceptions basé sur les filtres.|  
  
## <a name="remarks"></a>Remarques  

 Un tableau de `CoreDebugEHClause` valeurs est retourné par la méthode [getehclauses,](icordebugilcode-getehclauses-method.md) .  
  
 Les informations de la clause du gestionnaire d'exceptions sont définies par la spécification CLI. Pour plus d’informations, consultez [Standard ECMA-355 : Common Language Infrastructure (CLI), sixième édition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Le champ `flags` peut contenir les indicateurs suivants. Notez qu'ils ne sont pas définis dans CorDebug.idl ou CorDebug.h.  
  
|Indicateur|Valeur|Description|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Une clause d'exception typée.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Une clause de filtre et de gestionnaire d'exceptions.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|Une clause `finally`.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Une clause fault (une clause `finally` qui est appelée seulement quand une exception est levée).|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetEHClauses, méthode](icordebugilcode-getehclauses-method.md)
- [Structures de débogage](debugging-structures.md)
