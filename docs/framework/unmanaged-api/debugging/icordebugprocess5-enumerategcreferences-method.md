---
title: ICorDebugProcess5::EnumerateGCReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178618"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences, méthode
Obtient un enumérateur pour tous les objets qui doivent être collectés dans les ordures dans un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `enumerateWeakReferences`  
 [dans] Une valeur Boolean qui indique si des références faibles doivent également être énumérées. Si `enumerateWeakReferences` `true`c’est le cas, l’énumérateur `ppEnum` comprend à la fois des références fortes et des références faibles. Si `enumerateWeakReferences` `false`c’est le cas, l’énumérateur ne comprend que des références fortes.  
  
 `ppEnum`  
 [out] Un pointeur à l’adresse d’un [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) qui est un enumérateur pour les objets à collecter.  
  
## <a name="remarks"></a>Notes   
 Cette méthode fournit un moyen de déterminer la chaîne d’enracinement complète pour tout objet géré dans un processus et peut être utilisé pour déterminer pourquoi un objet est encore en vie.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess5, interface](icordebugprocess5-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
