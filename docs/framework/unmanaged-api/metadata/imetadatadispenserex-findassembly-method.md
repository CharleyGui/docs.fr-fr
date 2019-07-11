---
title: IMetaDataDispenserEx::FindAssembly, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85ebddf4ef96be2a583e54082e4d4405b30adf46
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777771"
---
# <a name="imetadatadispenserexfindassembly-method"></a>IMetaDataDispenserEx::FindAssembly, méthode
Cette méthode n’est pas implémentée. Si elle est appelée, elle retourne E_NOTIMPL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szAppBase`  
 [in] Non utilisé.  
  
 `szPrivateBin`  
 [in] Non utilisé.  
  
 `szGlobalBin`  
 [in] Non utilisé.  
  
 `szAssemblyName`  
 [in] L’assembly à rechercher.  
  
 `szName`  
 [out] Le nom simple de l’assembly.  
  
 `cchName`  
 [in] La taille, en octets, de `szName`.  
  
 `pcName`  
 [out] Le nombre de caractères réellement retournés dans `szName`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
