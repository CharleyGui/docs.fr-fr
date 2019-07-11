---
title: ICLRDataTarget::GetMachineType, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 958968fb1a84b598b0c3e92151fbad58fc5e79d4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738739"
---
# <a name="iclrdatatargetgetmachinetype-method"></a>ICLRDataTarget::GetMachineType, méthode
Obtient l’identificateur pour le genre de jeu d’instructions qui utilise le processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `machineType`  
 [out] Utilisation d’un pointeur vers une valeur qui indique le jeu d’instructions que le processus cible. Retourné `machineType` est une des constantes IMAGE_FILE_MACHINE qui sont définies dans le fichier d’en-tête WinNT.h.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
