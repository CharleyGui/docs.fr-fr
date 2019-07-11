---
title: RunDll32ShimW, fonction
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 569efa9d14ef10d8c5cf735091778a6c78882815
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781164"
---
# <a name="rundll32shimw-function"></a>RunDll32ShimW, fonction
Exécute la commande spécifiée.  
  
 Cette fonction a été déconseillée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hwnd`  
 [in] Un handle de fenêtre dans lequel la sortie de commande s’affiche.  
  
 `hinst`  
 [in] Handle vers la bibliothèque qui contient la commande.  
  
 `lpszCmdLine`  
 [in] Chaîne qui spécifie la commande à exécuter.  
  
 `nCmdShow`  
 [in] Entier qui spécifie le mode d’affichage de la fenêtre de sortie.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
