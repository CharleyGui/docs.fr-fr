---
title: ICLRDataTarget::GetImageBase, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dbb655d6ed0b9bd88c5eedf61a191401a805fb3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738758"
---
# <a name="iclrdatatargetgetimagebase-method"></a>ICLRDataTarget::GetImageBase, méthode
Obtient l’adresse mémoire de base de l’image spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `imagePath`  
 [in] Le nom de fichier de l’image, y compris son chemin d’accès.  
  
 `baseAddress`  
 [out] Pointeur vers un CLRDATA_ADDRESS qui stocke l’adresse de base de l’image.  
  
## <a name="remarks"></a>Notes  
 Le nom du fichier image peut ou ne peut pas avoir un chemin d’accès. Si un chemin d’accès est spécifié, le filtrage s’effectue sur le chemin d’accès complet ; Sinon, la correspondance s’effectue uniquement sur le nom de fichier.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
