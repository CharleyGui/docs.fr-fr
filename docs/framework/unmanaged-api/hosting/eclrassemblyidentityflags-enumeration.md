---
title: ECLRAssemblyIdentityFlags, énumération
ms.date: 03/30/2017
api_name:
- ECLRAssemblyIdentityFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECLRAssemblyIdentityFlags
helpviewer_keywords:
- ECLRAssemblyIdentityFlags enumeration [.NET Framework hosting]
ms.assetid: d1e0b654-ccaf-4fa2-9aa3-8e007813c84d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18b7310b2d04b81330c68de59adf5f18ba9c8675
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769755"
---
# <a name="eclrassemblyidentityflags-enumeration"></a>ECLRAssemblyIdentityFlags, énumération
Indique le type d’identité d’un assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _CLRAssemblyIdentityFlags {  
    CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT = 0  
} ECLRAssemblyIdentityFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT`|L’identité est rendue canonique.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
