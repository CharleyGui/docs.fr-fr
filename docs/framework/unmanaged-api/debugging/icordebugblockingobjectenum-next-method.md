---
title: ICorDebugBlockingObjectEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd82418da26ab0cd32b007b4613d588dfa695eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745292"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next, méthode
Obtient le nombre spécifié de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objets à partir de l’énumération, en commençant à la position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre d’objets à récupérer.  
  
 `values`  
 [out] Un tableau de pointeurs vers [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objets.  
  
 `pceltFetched`  
 [out] Pointeur vers le nombre d’objets qui ont été récupérées.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|S_FALSE|`pceltFetched` n’est pas égal à `celt`.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode fonctionne comme un énumérateur COM classique.  
  
 Les valeurs du tableau d’entrée doivent être au moins de taille `celt`. Le tableau est rempli avec une l’autre `celt` valeurs dans l’énumération ou avec toutes les valeurs restantes si moins de `celt` restent. Lorsque cette méthode est retournée, `pceltFetched` sera remplie avec le nombre de valeurs qui ont été récupérées. Si `values` contient des pointeurs non valides ou pointe vers une mémoire tampon qui est inférieure à `celt`, ou si `pceltFetched` est un pointeur non valide, le résultat est indéfini.  
  
> [!NOTE]
>  Bien que le [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure n’a pas besoin être libéré, l’interface « ICorDebugValue » qu’elle n’a besoin d’être publié.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
