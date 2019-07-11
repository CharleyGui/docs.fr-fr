---
title: IAssemblyCache::QueryAssemblyInfo, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a336e2d4516eaa43decf156f25a62729859a3ff0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778723"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a>IAssemblyCache::QueryAssemblyInfo, méthode
Obtient les données demandées sur l’assembly spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwFlags`  
 [in] Indicateurs définis dans Fusion.idl. Les valeurs suivantes sont prises en charge :  
  
- QUERYASMINFO_FLAG_VALIDATE (0x00000001)  
  
- QUERYASMINFO_FLAG_GETSIZE (0 X 00000002)  
  
 `pszAssemblyName`  
 [in] Le nom de l’assembly pour lequel les données seront récupérées.  
  
 `pAsmInfo`  
 [in, out] Un [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure qui contient les données relatives à l’assembly.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyCache, interface](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
