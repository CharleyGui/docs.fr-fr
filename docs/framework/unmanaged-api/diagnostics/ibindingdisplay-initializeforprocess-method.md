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
ms.openlocfilehash: f9e65b49c9a3b506cba3493d81a40f2759dca781
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725143"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess, méthode

Initialise l’objet [IBindingDisplay](ibindingdisplay-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pid`  
 dans Identificateur du processus.  
  
## <a name="remarks"></a>Remarques  

 Le débogueur appelle la `InitializeForProcess` méthode au moment de la création pour initialiser l’affichage de liaison. `InitializeForProcess` doit être appelé au moment de la création avant que toute autre méthode sur `IBindingDisplay` ne soit appelée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** BindingDisplay. h  
  
 **Bibliothèque :** BindingDisplay. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IBindingDisplay, interface](ibindingdisplay-interface.md)
