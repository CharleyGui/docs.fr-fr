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
ms.openlocfilehash: 4eb878b61b72378bc6870af7f2cd09f0b6943b13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136502"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="8ddfc-102">DestroyICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="8ddfc-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="8ddfc-103">Détruit un objet [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="8ddfc-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ddfc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ddfc-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ddfc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ddfc-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="8ddfc-107">dans Objet `ICeeFileGen` à détruire.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ddfc-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8ddfc-108">Return Value</span></span>  
 <span data-ttu-id="8ddfc-109">Cette méthode retourne des codes d’erreur COM standard.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ddfc-110">Notes</span><span class="sxs-lookup"><span data-stu-id="8ddfc-110">Remarks</span></span>  
 <span data-ttu-id="8ddfc-111">`DestroyICeeFileGen` détruit l’objet `ICeeFileGen` créé par la fonction [CreateICeeFileGen,](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ddfc-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="8ddfc-112">Requirements</span></span>  
 <span data-ttu-id="8ddfc-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ddfc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ddfc-114">**En-tête :** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="8ddfc-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="8ddfc-115">**Bibliothèque :** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="8ddfc-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="8ddfc-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ddfc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddfc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ddfc-117">See also</span></span>

- [<span data-ttu-id="8ddfc-118">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="8ddfc-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
