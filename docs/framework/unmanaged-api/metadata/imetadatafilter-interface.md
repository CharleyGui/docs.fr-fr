---
title: IMetaDataFilter, interface
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: 821936d20a421739e8eb3d5df228888df7f022e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503781"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="5d7df-102">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="5d7df-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="5d7df-103">Fournit des méthodes pour marquer et filtrer des jetons de métadonnées pour éviter de répéter des actions qui ont déjà été prises.</span><span class="sxs-lookup"><span data-stu-id="5d7df-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d7df-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5d7df-104">Methods</span></span>  
  
|<span data-ttu-id="5d7df-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5d7df-105">Method</span></span>|<span data-ttu-id="5d7df-106">Description</span><span class="sxs-lookup"><span data-stu-id="5d7df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d7df-107">IsTokenMarked, méthode</span><span class="sxs-lookup"><span data-stu-id="5d7df-107">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="5d7df-108">Obtient une valeur indiquant si le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="5d7df-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="5d7df-109">MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="5d7df-109">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="5d7df-110">Définit une valeur indiquant que le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="5d7df-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="5d7df-111">UnmarkAll, méthode</span><span class="sxs-lookup"><span data-stu-id="5d7df-111">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="5d7df-112">Supprime les marques de traitement de tous les jetons dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="5d7df-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d7df-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5d7df-113">Requirements</span></span>  
 <span data-ttu-id="5d7df-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d7df-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d7df-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5d7df-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d7df-116">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5d7df-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5d7df-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d7df-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7df-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d7df-118">See also</span></span>

- [<span data-ttu-id="5d7df-119">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="5d7df-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
