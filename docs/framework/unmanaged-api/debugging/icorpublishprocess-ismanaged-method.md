---
title: ICorPublishProcess::IsManaged, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790524"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged, méthode
Obtient une valeur qui indique si le processus référencé par ce [ICorPublishProcess](icorpublishprocess-interface.md) est connu pour avoir du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pbManaged`  
 à Pointeur vers une valeur booléenne qui indique si le processus a du code managé. La valeur est `true` si le processus a du code managé ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Étant donné que la version actuelle de `ICorPublishProcess` autorise l’accès uniquement aux processus qui ont du code managé, `IsManaged` retourne toujours `true`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorPublishProcess, interface](icorpublishprocess-interface.md)
