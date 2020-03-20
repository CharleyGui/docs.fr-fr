---
title: ICorDebugRegisterSet::GetRegisters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178541"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters, méthode
Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) qui est spécifié par le masque bit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mask`  
 [dans] Un masque qui précise quelles valeurs d’enregistrement doivent être récupérées. Chaque bit correspond à un registre. Si un peu est réglé à un, la valeur du registre est récupérée; autrement, la valeur du registre n’est pas récupérée.  
  
 `regCount`  
 [dans] Nombre de valeurs de registre à récupérer.  
  
 `regBuffer`  
 [out] Une gamme `CORDB_REGISTER` d’objets, dont chacun reçoit une valeur d’un registre.  
  
## <a name="remarks"></a>Notes   
 La taille du tableau doit être égale au nombre de bits réglés à un dans le masque de bit. Le `regCount` paramètre précise le nombre d’éléments dans le tampon qui recevront les valeurs du registre. Si `regCount` la valeur est trop faible pour le nombre de registres indiqués par le masque, les registres numérotés plus élevés seront tronqués à partir de l’ensemble. Si `regCount` la valeur est trop `regBuffer` grande, les éléments inutilisés ne seront pas modifiés.  
  
 Si le masque bit spécifie `GetRegisters` un registre qui n’est pas disponible, renvoie une valeur indéterminée pour ce registre.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interface](icordebugregisterset2-interface.md)
