---
title: CreateICeeFileGen, fonction
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: de27851b4afc3eccad46531848c68723bff346d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136822"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="4324e-102">CreateICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="4324e-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="4324e-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span><span class="sxs-lookup"><span data-stu-id="4324e-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="4324e-104">This function has been deprecated in the .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4324e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4324e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4324e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4324e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4324e-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="4324e-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span><span class="sxs-lookup"><span data-stu-id="4324e-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4324e-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4324e-108">Return Value</span></span>  
 <span data-ttu-id="4324e-109">This method returns standard COM error codes.</span><span class="sxs-lookup"><span data-stu-id="4324e-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4324e-110">Notes</span><span class="sxs-lookup"><span data-stu-id="4324e-110">Remarks</span></span>  
 <span data-ttu-id="4324e-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span><span class="sxs-lookup"><span data-stu-id="4324e-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="4324e-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span><span class="sxs-lookup"><span data-stu-id="4324e-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4324e-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="4324e-113">Requirements</span></span>  
 <span data-ttu-id="4324e-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4324e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4324e-115">**Header:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="4324e-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="4324e-116">**Library:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="4324e-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="4324e-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4324e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4324e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4324e-118">See also</span></span>

- [<span data-ttu-id="4324e-119">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="4324e-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
