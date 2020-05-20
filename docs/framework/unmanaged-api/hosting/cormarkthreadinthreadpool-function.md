---
title: CorMarkThreadInThreadPool, fonction
ms.date: 03/30/2017
api_name:
- CorMarkThreadInThreadPool
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorMarkThreadInThreadPool
helpviewer_keywords:
- CorMarkThreadInThreadPool function [.NET Framework hosting]
ms.assetid: 3f958d41-e82e-4ec3-ae6f-16c7b3b31e3e
topic_type:
- apiref
ms.openlocfilehash: 30e8df6e2dcdfed15badaa6c0996ee6c912315d2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616520"
---
# <a name="cormarkthreadinthreadpool-function"></a>CorMarkThreadInThreadPool, fonction
Marque le thread du pool de threads en cours d’exécution pour l’exécution du code managé. À partir de la version 2,0 de .NET Framework, cette fonction n’a aucun effet. Elle n’est pas obligatoire et peut être supprimée de votre code. Cette fonction est déconseillée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
