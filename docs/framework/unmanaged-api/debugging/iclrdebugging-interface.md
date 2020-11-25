---
title: ICLRDebugging, interface
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 6eea7f6c222b8e30376ec72ee0c193a68c23f0d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723556"
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging, interface

Fournit des méthodes qui gèrent le chargement et le déchargement des modules pour le débogage.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[OpenVirtualProcess, méthode](iclrdebugging-openvirtualprocess-method.md)|Obtient l’interface « ICorDebugProcess » qui correspond à un module common language runtime (CLR) chargé dans le processus.|  
|[CanUnloadNow, méthode](iclrdebugging-canunloadnow-method.md)|Détermine si une bibliothèque qui a été fournie par une interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) est toujours en cours d’utilisation ou si elle peut être déchargée.|  
  
## <a name="remarks"></a>Remarques  

 Vous pouvez obtenir une instance de l' `ICLRDebugging` interface à l’aide de la fonction [CLRCreateInstance](../hosting/clrcreateinstance-function.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
