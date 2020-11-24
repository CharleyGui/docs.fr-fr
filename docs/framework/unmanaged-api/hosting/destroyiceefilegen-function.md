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
ms.openlocfilehash: 495d84470c559df13ea64b63dd00582f4335d4e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673175"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="09f71-102">DestroyICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="09f71-102">DestroyICeeFileGen Function</span></span>

<span data-ttu-id="09f71-103">Détruit un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="09f71-103">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="09f71-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="09f71-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f71-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09f71-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09f71-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09f71-106">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="09f71-107">dans `ICeeFileGen` Objet à détruire.</span><span class="sxs-lookup"><span data-stu-id="09f71-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09f71-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="09f71-108">Return Value</span></span>  

 <span data-ttu-id="09f71-109">Cette méthode retourne des codes d’erreur COM standard.</span><span class="sxs-lookup"><span data-stu-id="09f71-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09f71-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="09f71-110">Remarks</span></span>  

 <span data-ttu-id="09f71-111">`DestroyICeeFileGen` détruit l' `ICeeFileGen` objet créé par la fonction [CreateICeeFileGen,](createiceefilegen-function.md) .</span><span class="sxs-lookup"><span data-stu-id="09f71-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09f71-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="09f71-112">Requirements</span></span>  

 <span data-ttu-id="09f71-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09f71-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09f71-114">**En-tête :** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="09f71-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="09f71-115">**Bibliothèque :** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="09f71-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="09f71-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09f71-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f71-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09f71-117">See also</span></span>

- [<span data-ttu-id="09f71-118">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="09f71-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
