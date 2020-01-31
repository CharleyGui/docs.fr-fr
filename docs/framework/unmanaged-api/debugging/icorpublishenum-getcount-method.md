---
title: ICorPublishEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
ms.openlocfilehash: 0b3754fbcca50b52039dc358aed7070b8a152ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790633"
---
# <a name="icorpublishenumgetcount-method"></a>ICorPublishEnum::GetCount, méthode
Obtient le nombre d’éléments dans l’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pcelt`  
 à Pointeur vers le nombre d’éléments dans l’énumération.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublishEnum, interface](icorpublishenum-interface.md)
