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
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="2a865-102">IAssemblyName::GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="2a865-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="2a865-103">Obtient les informations de version pour l’assembly référencé par ce [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="2a865-103">Gets the version information for the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a865-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a865-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a865-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2a865-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="2a865-106">[out] 32 bits de poids fort de la version.</span><span class="sxs-lookup"><span data-stu-id="2a865-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="2a865-107">[out] 32 bits de poids faibles de la version.</span><span class="sxs-lookup"><span data-stu-id="2a865-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a865-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2a865-108">Requirements</span></span>  
 <span data-ttu-id="2a865-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a865-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a865-110">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2a865-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2a865-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a865-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a865-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a865-112">See also</span></span>

- [<span data-ttu-id="2a865-113">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="2a865-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
