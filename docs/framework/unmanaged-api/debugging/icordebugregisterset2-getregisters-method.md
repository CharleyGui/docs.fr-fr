---
title: ICorDebugRegisterSet2::GetRegisters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c1b90390689e709ee131935bd6417fa6b273eb2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769985"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters, méthode
Obtient la valeur de chaque registre (pour la plateforme sur laquelle le code est en cours d’exécution) qui est spécifié par le masque de bits donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `maskCount`  
 [in] La taille, en octets, de la `mask` tableau.  
  
 `mask`  
 [in] Tableau d’octets, dont chaque bit correspond à un Registre. Si le bit est 1, valeur de Registre correspondantes est récupérée.  
  
 `regCount`  
 [in] Le nombre de valeurs de registres à récupérer.  
  
 `regBuffer`  
 [out] Un tableau de `CORDB_REGISTER` objets, chacun d'entre eux reçoit la valeur d’un Registre.  
  
## <a name="remarks"></a>Notes  
 Le `GetRegisters` méthode retourne un tableau de valeurs à partir des registres qui sont spécifiés par le masque. Le tableau ne contient pas les valeurs des registres dont le bit masque n’est pas défini. Par conséquent, la taille de la `regBuffer` tableau doit être égal au nombre de 1 dans le masque. Si la valeur de `regCount` est trop petite pour le nombre de registres indiqué par le masque, les valeurs les plus élevées des registres est tronqué de l’ensemble. Si `regCount` est trop volumineux, l’inutilisé `regBuffer` éléments ne sont pas modifiés.  
  
 Si un Registre non disponible est indiqué par le masque, une valeur indéterminée s’affichera pour ce Registre.  
  
 Le `ICorDebugRegisterSet2::GetRegisters` méthode est nécessaire pour les plateformes qui ont plus de 64 registres. Par exemple, IA64 comporte 128 registres à usage général et 128 registres en virgule flottante, et vous devez donc plus de 64 bits dans le masque de bits.  
  
 Si vous n’avez pas plus de 64 registres, comme c’est le cas sur les plateformes, telles que x86, le `GetRegisters` méthode traduit en fait juste les octets dans le `mask` tableau d’octets dans un `ULONG64` , puis appelle le [ICorDebugRegisterSet :: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) (méthode), qui prend le `ULONG64` masque.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRegisterSet2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
