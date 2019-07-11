---
title: DestroyICeeFileGen, fonction
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab4560774edce49341c86dd9446e38701db7fa62
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769821"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="01ba3-102">DestroyICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="01ba3-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="01ba3-103">Détruit un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objet.</span><span class="sxs-lookup"><span data-stu-id="01ba3-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="01ba3-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="01ba3-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ba3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01ba3-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01ba3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01ba3-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="01ba3-107">[in] Le `ICeeFileGen` objet à détruire.</span><span class="sxs-lookup"><span data-stu-id="01ba3-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01ba3-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="01ba3-108">Return Value</span></span>  
 <span data-ttu-id="01ba3-109">Cette méthode retourne des codes d’erreur COM standard.</span><span class="sxs-lookup"><span data-stu-id="01ba3-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01ba3-110">Notes</span><span class="sxs-lookup"><span data-stu-id="01ba3-110">Remarks</span></span>  
 <span data-ttu-id="01ba3-111">`DestroyICeeFileGen` détruit le `ICeeFileGen` objet créé par le [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="01ba3-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01ba3-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="01ba3-112">Requirements</span></span>  
 <span data-ttu-id="01ba3-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01ba3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01ba3-114">**En-tête :** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="01ba3-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="01ba3-115">**Bibliothèque :** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="01ba3-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="01ba3-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01ba3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ba3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01ba3-117">See also</span></span>

- [<span data-ttu-id="01ba3-118">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="01ba3-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
