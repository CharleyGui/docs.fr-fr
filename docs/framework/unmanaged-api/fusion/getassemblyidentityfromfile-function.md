---
title: GetAssemblyIdentityFromFile, fonction
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 50ec5a23db4d2460480bcc3e463ecd88e7470bde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134531"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="d5928-102">GetAssemblyIdentityFromFile, fonction</span><span class="sxs-lookup"><span data-stu-id="d5928-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="d5928-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span><span class="sxs-lookup"><span data-stu-id="d5928-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5928-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5928-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5928-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d5928-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="d5928-106">[in] A valid path to the requested assembly.</span><span class="sxs-lookup"><span data-stu-id="d5928-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="d5928-107">[in] The `IID` of the interface to return.</span><span class="sxs-lookup"><span data-stu-id="d5928-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="d5928-108">[out] The returned interface pointer.</span><span class="sxs-lookup"><span data-stu-id="d5928-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5928-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="d5928-109">Requirements</span></span>  
 <span data-ttu-id="d5928-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5928-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5928-111">**Header:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d5928-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d5928-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5928-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5928-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5928-113">See also</span></span>

- [<span data-ttu-id="d5928-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="d5928-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="d5928-115">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="d5928-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
