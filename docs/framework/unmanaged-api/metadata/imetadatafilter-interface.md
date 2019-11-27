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
ms.openlocfilehash: e8b15f478eb3b94b7cdcab3b69d54e7cc99be13b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440165"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="03024-102">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="03024-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="03024-103">Fournit des méthodes pour marquer et filtrer des jetons de métadonnées pour éviter de répéter des actions qui ont déjà été prises.</span><span class="sxs-lookup"><span data-stu-id="03024-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03024-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="03024-104">Methods</span></span>  
  
|<span data-ttu-id="03024-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="03024-105">Method</span></span>|<span data-ttu-id="03024-106">Description</span><span class="sxs-lookup"><span data-stu-id="03024-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03024-107">IsTokenMarked, méthode</span><span class="sxs-lookup"><span data-stu-id="03024-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="03024-108">Obtient une valeur indiquant si le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="03024-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="03024-109">MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="03024-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="03024-110">Définit une valeur indiquant que le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="03024-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="03024-111">UnmarkAll, méthode</span><span class="sxs-lookup"><span data-stu-id="03024-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="03024-112">Supprime les marques de traitement de tous les jetons dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="03024-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03024-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="03024-113">Requirements</span></span>  
 <span data-ttu-id="03024-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03024-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03024-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="03024-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03024-116">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03024-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03024-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03024-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03024-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03024-118">See also</span></span>

- [<span data-ttu-id="03024-119">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="03024-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
