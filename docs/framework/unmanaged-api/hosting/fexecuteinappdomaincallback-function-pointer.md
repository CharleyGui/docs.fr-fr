---
title: FExecuteInAppDomainCallback (pointeur fonction)
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3de456bc28f51cb20ab72b3934041ec6b06ae
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490441"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a>FExecuteInAppDomainCallback (pointeur fonction)
Pointe vers une fonction qui est appelée par le common language runtime (CLR) pour exécuter le code managé.  
  
 Ce pointeur de fonction a été déconseillé dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cookie`  
 [in] Un pointeur vers la mémoire allouée par l’appelant opaque qui contient le code managé doit être exécuté.  
  
 L’allocation et la durée de vie de cette mémoire sont contrôlées par l’appelant (autrement dit, le CLR). Cela n’est pas mémoire de tas managé CLR.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorWks.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
