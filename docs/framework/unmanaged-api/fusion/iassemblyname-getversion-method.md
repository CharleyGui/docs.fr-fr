---
title: IAssemblyName::GetVersion, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5b5f7ce6a4ce8f542b3c49fe4749bfde23ecf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744492"
---
# <a name="iassemblynamegetversion-method"></a>IAssemblyName::GetVersion, méthode
Obtient les informations de version pour l’assembly référencé par ce [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pdwVersionHi`  
 [out] 32 bits de poids fort de la version.  
  
 `pdwVersionLow`  
 [out] 32 bits de poids faibles de la version.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyName, interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
