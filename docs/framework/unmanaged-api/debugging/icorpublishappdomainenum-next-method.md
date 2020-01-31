---
title: ICorPublishAppDomainEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: c8866e98be0dd064138acdf5e0f6fb9c339fb3d2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790646"
---
# <a name="icorpublishappdomainenumnext-method"></a>ICorPublishAppDomainEnum::Next, méthode
Obtient le nombre spécifié de domaines d’application qui existent actuellement dans le processus, en commençant à la position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `celt`  
 dans Nombre d’éléments à récupérer.  
  
 `objects`  
 à Pointeur vers le tableau d’objets [ICorPublishAppDomain](icorpublishappdomain-interface.md) récupérés, chacun représentant un domaine d’application.  
  
 `pceltFetched`  
 à Pointeur vers le nombre de domaines d’application réellement retournés. Cette valeur peut être null si `celt` est un.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublishAppDomainEnum, interface](icorpublishappdomainenum-interface.md)
