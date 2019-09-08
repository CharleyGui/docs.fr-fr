---
title: IAssemblyName::GetProperty, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 351d540d226f46f180b46323e83eb1bcc71da4f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796587"
---
# <a name="iassemblynamegetproperty-method"></a>IAssemblyName::GetProperty, méthode
Obtient un pointeur vers la propriété référencée par l’identificateur de propriété spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `PropertyId`  
 dans Identificateur unique de la propriété demandée.  
  
 `pvProperty`  
 à Données de propriété retournées.  
  
 `pcbProperty`  
 [in, out] Taille, en octets, de `pvProperty`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyName, interface](iassemblyname-interface.md)
