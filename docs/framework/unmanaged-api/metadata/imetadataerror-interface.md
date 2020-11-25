---
title: IMetaDataError, interface
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
ms.openlocfilehash: 5f5e04787ce0ab0e1c8ecf3c19ba37e76ba38bfe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701924"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="118fb-102">IMetaDataError, interface</span><span class="sxs-lookup"><span data-stu-id="118fb-102">IMetaDataError Interface</span></span>

<span data-ttu-id="118fb-103">Fournit un mécanisme de rappel pour signaler les erreurs pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="118fb-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="118fb-104">L' `IMetaDataError` interface doit être implémentée par le client.</span><span class="sxs-lookup"><span data-stu-id="118fb-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="118fb-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="118fb-105">Methods</span></span>  
  
|<span data-ttu-id="118fb-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="118fb-106">Method</span></span>|<span data-ttu-id="118fb-107">Description</span><span class="sxs-lookup"><span data-stu-id="118fb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="118fb-108">OnError, méthode</span><span class="sxs-lookup"><span data-stu-id="118fb-108">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="118fb-109">Fournit une notification des erreurs qui se produisent pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="118fb-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="118fb-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="118fb-110">Requirements</span></span>  

 <span data-ttu-id="118fb-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="118fb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="118fb-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="118fb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="118fb-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="118fb-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="118fb-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="118fb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="118fb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="118fb-115">See also</span></span>

- [<span data-ttu-id="118fb-116">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="118fb-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
