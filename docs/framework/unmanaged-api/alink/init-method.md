---
title: Init, méthode
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
ms.openlocfilehash: 25a1c29ab94a785304b83d5b1bcb2d7176742a68
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726016"
---
# <a name="init-method"></a><span data-ttu-id="52b6c-102">Init, méthode</span><span class="sxs-lookup"><span data-stu-id="52b6c-102">Init Method</span></span>

<span data-ttu-id="52b6c-103">Prépare les objets qui implémentent l' [interface IALink](ialink-interface.md) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="52b6c-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52b6c-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="52b6c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="52b6c-105">Parameters</span></span>  

 `pDispenser`  
 <span data-ttu-id="52b6c-106">[IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) pointeur d’interface vers le distributeur de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="52b6c-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="52b6c-107">Pointeur d' [interface IMetaDataError](../metadata/imetadataerror-interface.md) vers une interface de gestion des erreurs facultative.</span><span class="sxs-lookup"><span data-stu-id="52b6c-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52b6c-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="52b6c-108">Return Value</span></span>  

 <span data-ttu-id="52b6c-109">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="52b6c-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52b6c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="52b6c-110">Requirements</span></span>  

 <span data-ttu-id="52b6c-111">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="52b6c-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b6c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52b6c-112">See also</span></span>

- [<span data-ttu-id="52b6c-113">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="52b6c-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="52b6c-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="52b6c-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="52b6c-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="52b6c-115">ALink API</span></span>](index.md)
