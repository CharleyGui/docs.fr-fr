---
title: EmitInternalExportedTypes, méthode
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15174480c4345f2514572701a5525f0f192ad120
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742103"
---
# <a name="emitinternalexportedtypes-method"></a>EmitInternalExportedTypes, méthode
Émet des types ajoutés à l’assembly. Appelez cette méthode une fois connu types internes ont été ajoutés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Nécessite alink.h  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
