---
title: ICorDebugRegisterSet2::GetRegistersAvailable, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: 2149c985519b95f89af2c50d05753ae7259babe4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378220"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable, méthode
Obtient un tableau d’octets qui fournit une bitmap des registres disponibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `numChunks`  
 [in] Taille du tableau `availableRegChunks`.  
  
 `availableRegChunks`  
 à Tableau d’octets, chacun d’eux correspondant à un registre. Si un registre est disponible, le bit correspondant du Registre est défini.  
  
## <a name="remarks"></a>Remarks  
 Les valeurs de l’énumération CorDebugRegister spécifient les registres de différents microprocesseurs. Les cinq bits supérieurs de chaque valeur correspondent à l’index dans le `availableRegChunks` tableau d’octets. Les trois bits de poids faible de chaque valeur identifient la position du bit dans l’octet indexé. À partir d’une `CorDebugRegister` valeur qui spécifie un registre particulier, la position du Registre dans le masque est déterminée comme suit :  
  
1. Extrayez l’index nécessaire pour accéder à l’octet correct dans le `availableRegChunks` tableau :  
  
     `CorDebugRegister`valeur >> 3  
  
2. Extrayez la position du bit dans l’octet indexé, où le bit zéro est le bit le moins significatif :  
  
     `CorDebugRegister`valeur & 7  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRegisterSet2, interface](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)
