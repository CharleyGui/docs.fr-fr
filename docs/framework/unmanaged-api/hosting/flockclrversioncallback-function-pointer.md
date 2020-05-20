---
title: FLockClrVersionCallback (pointeur fonction)
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: af42de820b2d835e8ea137a2643a51678e382ff0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617280"
---
# <a name="flockclrversioncallback-function-pointer"></a>FLockClrVersionCallback (pointeur fonction)
Pointe vers une fonction que le common language runtime (CLR) appelle pour indiquer que l’initialisation a démarré ou est terminée.  
  
 Ce pointeur de fonction est déconseillé dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction est implémentée par l’hôte.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorWks. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [LockClrVersion, fonction](lockclrversion-function.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
