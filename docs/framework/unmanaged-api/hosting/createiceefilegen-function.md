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
ms.openlocfilehash: 294b82efd66704014aab1b73171afe9165f17664
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616448"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="32430-102">CreateICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="32430-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="32430-103">Crée un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="32430-103">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="32430-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="32430-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32430-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32430-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32430-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="32430-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="32430-107">à Pointeur vers l’adresse d’un nouvel `ICeeFileGen` objet.</span><span class="sxs-lookup"><span data-stu-id="32430-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32430-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="32430-108">Return Value</span></span>  
 <span data-ttu-id="32430-109">Cette méthode retourne des codes d’erreur COM standard.</span><span class="sxs-lookup"><span data-stu-id="32430-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32430-110">Notes</span><span class="sxs-lookup"><span data-stu-id="32430-110">Remarks</span></span>  
 <span data-ttu-id="32430-111">L' `ICeeFileGen` objet permet de créer des fichiers exécutables portables (PE, Portable Executable) Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="32430-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="32430-112">Appelez la fonction [DestroyICeeFileGen,](destroyiceefilegen-function.md) pour détruire l' `ICeeFileGen` objet une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="32430-112">Call the [DestroyICeeFileGen](destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32430-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="32430-113">Requirements</span></span>  
 <span data-ttu-id="32430-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32430-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32430-115">**En-tête :** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="32430-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="32430-116">**Bibliothèque :** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="32430-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="32430-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32430-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32430-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32430-118">See also</span></span>

- [<span data-ttu-id="32430-119">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="32430-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
