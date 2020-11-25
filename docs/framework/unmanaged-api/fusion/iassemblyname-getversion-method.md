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
ms.openlocfilehash: 6f37979c7a4873a7751db0296dc7d485c3444561
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715899"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="02d55-102">IAssemblyName::GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="02d55-102">IAssemblyName::GetVersion Method</span></span>

<span data-ttu-id="02d55-103">Obtient les informations de version de l’assembly référencé par cet objet [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="02d55-103">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02d55-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02d55-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02d55-105">Parameters</span></span>  

 `pdwVersionHi`  
 <span data-ttu-id="02d55-106">à 32 bits de poids fort de la version.</span><span class="sxs-lookup"><span data-stu-id="02d55-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="02d55-107">à Les 32 bits de version basse de la version.</span><span class="sxs-lookup"><span data-stu-id="02d55-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02d55-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="02d55-108">Requirements</span></span>  

 <span data-ttu-id="02d55-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02d55-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02d55-110">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="02d55-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="02d55-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02d55-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d55-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02d55-112">See also</span></span>

- [<span data-ttu-id="02d55-113">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="02d55-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
