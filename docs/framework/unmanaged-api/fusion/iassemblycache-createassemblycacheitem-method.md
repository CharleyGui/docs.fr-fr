---
title: IAssemblyCache::CreateAssemblyCacheItem, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a19ea52007edcc1930a2be46059a35b9cbebdc52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650393"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a>IAssemblyCache::CreateAssemblyCacheItem, méthode
Obtient une référence à un nouveau [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwFlags`  
 [in] Indicateurs définis dans Fusion.idl. Les valeurs suivantes sont prises en charge :  
  
- IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)  
  
- IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)  
  
 `pvReserved`  
 [in] Réservé pour une extensibilité future. `pvReserved` doit être une référence null.  
  
 `ppAsmItem`  
 [out] Retourné `IAssemblyCacheItem` pointeur.  
  
 `pszAssemblyName`  
 [in, optional] Rendu non canonique, séparés par des virgules `name=value` paires.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAssemblyCache, interface](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [IAssemblyCacheItem, interface](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
