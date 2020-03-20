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
ms.openlocfilehash: 6f7f400c51ded0b98c0c2286cb6f90bbd77e47d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178398"
---
# <a name="icorpublishappdomainenumnext-method"></a>ICorPublishAppDomainEnum::Next, méthode
Obtient le nombre spécifié de domaines d’application qui existent actuellement dans le processus, à partir de la position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `celt`  
 [dans] Nombre d’éléments à récupérer.  
  
 `objects`  
 [out] Un pointeur à la gamme d’objets [ICorPublishAppDomain](icorpublishappdomain-interface.md) récupérés, dont chacun représente un domaine d’application.  
  
 `pceltFetched`  
 [out] Pointeur sur le nombre de domaines d’application effectivement retourné. Cette valeur peut `celt` être nulle si elle en est une.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorPub.idl, CorPub.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublishAppDomainEnum, interface](icorpublishappdomainenum-interface.md)
