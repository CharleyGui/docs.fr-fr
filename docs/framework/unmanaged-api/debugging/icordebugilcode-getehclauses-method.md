---
title: ICorDebugILCode::GetEHClauses, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: e1fd68cd079b381d941d416831133c54e49ac48a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210382"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Retourne un pointeur vers une liste de clauses de gestion des exceptions qui sont définies pour ce langage intermédiaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cClauses`  
 [en entrée] La capacité de stockage du tableau `clauses`. Pour plus d'informations, consultez la section Remarques.  
  
 `pcClauses`  
 [en sortie] Le nombre de clauses à propos desquelles des informations sont écrites dans le tableau `clauses`.  
  
 clauses  
 à Tableau d’objets [CorDebugEHClause](cordebugehclause-structure.md) qui contiennent des informations sur les clauses de gestion des exceptions définies pour ce langage intermédiaire.  
  
## <a name="remarks"></a>Remarks  
 Si `cClauses` a la valeur 0 et que `pcClauses` est non**null**, `pcClauses` a pour valeur le nombre de clauses de gestion des exceptions disponibles. Si `cClauses` est différent de zéro, il représente la capacité de stockage du tableau `clauses`. Quand la méthode se termine, `clauses` contient un maximum de `cClauses` éléments et `pcClauses` est défini avec le nombre de clauses réellement écrites dans le tableau `clauses`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugILCode, interface](icordebugilcode-interface.md)
- [CorDebugEHClause, structure](cordebugehclause-structure.md)
- [Interfaces de débogage](debugging-interfaces.md)
