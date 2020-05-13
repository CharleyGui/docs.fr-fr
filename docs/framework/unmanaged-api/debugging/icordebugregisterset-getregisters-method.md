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
ms.openlocfilehash: 40de06d47654337542d2c80dc325f8201335312a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379152"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters, méthode
Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) spécifié par le masque de bits.  
  
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
 dans Masque de bits qui spécifie les valeurs de Registre à récupérer. Chaque bit correspond à un registre. Si un bit est défini sur un, la valeur du Registre est Récupérée ; dans le cas contraire, la valeur du Registre n’est pas récupérée.  
  
 `regCount`  
 dans Nombre de valeurs de Registre à récupérer.  
  
 `regBuffer`  
 à Tableau d' `CORDB_REGISTER` objets, chacun d’entre eux recevant une valeur d’un registre.  
  
## <a name="remarks"></a>Remarks  
 La taille du tableau doit être égale au nombre de bits défini sur un dans le masque de bits. Le `regCount` paramètre spécifie le nombre d’éléments dans la mémoire tampon qui recevront les valeurs de registre. Si la `regCount` valeur est trop petite pour le nombre de registres indiqué par le masque, les registres numérotés les plus élevés seront tronqués de l’ensemble. Si la `regCount` valeur est trop grande, les éléments inutilisés `regBuffer` ne seront pas modifiés.  
  
 Si le masque de bits spécifie un registre qui n’est pas disponible, `GetRegisters` retourne une valeur indéterminée pour ce registre.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interface](icordebugregisterset2-interface.md)
