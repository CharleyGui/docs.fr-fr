---
title: IAssemblyCacheItem::Commit, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
ms.openlocfilehash: f840438e175790a2b4c97302963b910f98dffb7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176563"
---
# <a name="iassemblycacheitemcommit-method"></a>IAssemblyCacheItem::Commit, méthode
Engage la référence d’assemblage mise en cache à la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwFlags`  
 [dans] Drapeaux définis dans Fusion.idl.  
  
 `pulDisposition`  
 [out, facultatif] Une valeur qui indique le résultat de l’opération.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** Fusion.h  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyCacheItem, interface](iassemblycacheitem-interface.md)
