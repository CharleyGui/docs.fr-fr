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
ms.openlocfilehash: 54a5fb50a0177fe9886582c112f16ce871ea9df4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792066"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters, méthode
Obtient la valeur de chaque registre (pour la plateforme sur laquelle le code est en cours d’exécution) spécifié par le masque de bits donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `maskCount`  
 dans Taille, en octets, du tableau de `mask`.  
  
 `mask`  
 dans Tableau d’octets, chacun d’eux correspondant à un registre. Si le bit est 1, la valeur du Registre correspondant est récupérée.  
  
 `regCount`  
 dans Nombre de valeurs de Registre à récupérer.  
  
 `regBuffer`  
 à Tableau d’objets `CORDB_REGISTER`, chacun d’entre eux recevant la valeur d’un registre.  
  
## <a name="remarks"></a>Notes  
 La méthode `GetRegisters` retourne un tableau de valeurs à partir des registres spécifiés par le masque. Le tableau ne contient pas de valeurs de registres dont le bit de masque n’est pas défini. Par conséquent, la taille du tableau de `regBuffer` doit être égale au nombre de 1 dans le masque. Si la valeur de `regCount` est trop petite pour le nombre de registres indiqué par le masque, les valeurs des registres numérotés les plus élevés sont tronquées de l’ensemble. Si `regCount` est trop grande, les éléments `regBuffer` inutilisés ne seront pas modifiés.  
  
 Si un registre non disponible est indiqué par le masque, une valeur indéterminée est retournée pour ce registre.  
  
 La méthode `ICorDebugRegisterSet2::GetRegisters` est nécessaire pour les plateformes qui ont plus de 64 registres. Par exemple, IA64 a des registres à usage général 128 et des registres à virgule flottante 128. vous avez donc besoin de plus de 64 bits dans le masque de bits.  
  
 Si vous n’avez pas plus de 64 registres, comme c’est le cas sur les plateformes telles que x86, la méthode `GetRegisters` convertit en fait simplement les octets du tableau d’octets `mask` en un `ULONG64`, puis appelle la méthode [ICorDebugRegisterSet :: GetRegisters,](icordebugregisterset-getregisters-method.md) , qui prend le masque `ULONG64`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRegisterSet2, interface](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)
