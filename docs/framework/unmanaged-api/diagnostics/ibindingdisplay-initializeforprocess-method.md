---
title: IBindingDisplay::InitializeForProcess, méthode
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: bb796a12868cc3e44394ab493f7838dc48ab4dc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448486"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess, méthode
Initialise l’objet [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pid`  
 dans Identificateur du processus.  
  
## <a name="remarks"></a>Notes  
 Le débogueur appelle la méthode `InitializeForProcess` au moment de la création pour initialiser l’affichage de liaison. `InitializeForProcess` doit être appelée au moment de la création avant que toute autre méthode sur `IBindingDisplay` soit appelée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** BindingDisplay. h  
  
 **Bibliothèque :** BindingDisplay. idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IBindingDisplay, interface](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
