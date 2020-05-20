---
title: IBindingDisplay::GetCurrentDisplay, méthode
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442187"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a>IBindingDisplay::GetCurrentDisplay, méthode
Retourne les informations d’affichage de liaison actuelles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `display`  
 [out, retval] Pointeur vers un SafeArray contenant les informations d’affichage de liaison.  
  
## <a name="remarks"></a>Notes  
 La méthode [IBindingDisplay :: InitializeForProcess,](ibindingdisplay-initializeforprocess-method.md) doit avoir déjà réussi et le programme doit être arrêté par un débogueur.  
  
 L’appelant doit libérer la mémoire retournée `SAFEARRAY` à l’aide de [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** BindingDisplay. h  
  
 **Bibliothèque :** BindingDisplay. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IBindingDisplay, interface](ibindingdisplay-interface.md)
- [InitializeForProcess, méthode](ibindingdisplay-initializeforprocess-method.md)
