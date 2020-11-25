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
ms.openlocfilehash: 232068a5fee8f7bd3dfbddf4d9452e80d6fd6170
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719188"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next, méthode

Obtient le nombre spécifié d’objets [CorDebugBlockingObject](cordebugblockingobject-structure.md) à partir de l’énumération, en commençant à la position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>Paramètres  

 `celt`  
 dans Nombre d’objets à récupérer.  
  
 `values`  
 à Tableau de pointeurs vers des objets [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
 `pceltFetched`  
 à Pointeur vers le nombre d’objets qui ont été récupérés.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|S_FALSE|`pceltFetched` n’est pas égal à `celt`.|  
  
## <a name="remarks"></a>Remarques  

 Cette méthode fonctionne comme un énumérateur COM classique.  
  
 Les valeurs du tableau d’entrée doivent être au moins de la taille `celt` . Le tableau sera rempli avec les `celt` valeurs suivantes dans l’énumération ou avec toutes les valeurs restantes si elles sont inférieures à `celt` . Lorsque cette méthode est retournée, `pceltFetched` est rempli avec le nombre de valeurs qui ont été récupérées. Si `values` contient des pointeurs non valides ou pointe vers une mémoire tampon inférieure à `celt` , ou si `pceltFetched` est un pointeur non valide, le résultat n’est pas défini.  
  
> [!NOTE]
> Bien que la structure [CorDebugBlockingObject](cordebugblockingobject-structure.md) n’ait pas besoin d’être libérée, l’interface « ICorDebugValue » à l’intérieur de celle-ci doit être libérée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget, interface](icordebugdatatarget-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
