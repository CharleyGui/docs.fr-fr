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
ms.openlocfilehash: ff7e7b299d185b8db263d2076c1e075b87b487fc
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616396"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="13f64-102">DestroyICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="13f64-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="13f64-103">Détruit un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="13f64-103">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="13f64-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="13f64-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f64-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13f64-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13f64-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="13f64-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="13f64-107">dans `ICeeFileGen`Objet à détruire.</span><span class="sxs-lookup"><span data-stu-id="13f64-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13f64-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="13f64-108">Return Value</span></span>  
 <span data-ttu-id="13f64-109">Cette méthode retourne des codes d’erreur COM standard.</span><span class="sxs-lookup"><span data-stu-id="13f64-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13f64-110">Notes</span><span class="sxs-lookup"><span data-stu-id="13f64-110">Remarks</span></span>  
 <span data-ttu-id="13f64-111">`DestroyICeeFileGen`détruit l' `ICeeFileGen` objet créé par la fonction [CreateICeeFileGen,](createiceefilegen-function.md) .</span><span class="sxs-lookup"><span data-stu-id="13f64-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13f64-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="13f64-112">Requirements</span></span>  
 <span data-ttu-id="13f64-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13f64-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f64-114">**En-tête :** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="13f64-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="13f64-115">**Bibliothèque :** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="13f64-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="13f64-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f64-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f64-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13f64-117">See also</span></span>

- [<span data-ttu-id="13f64-118">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="13f64-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
