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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf96770dd58c9b84596c082a615f626ec723cc6c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787251"
---
# <a name="init-method"></a><span data-ttu-id="b3b78-102">Init, méthode</span><span class="sxs-lookup"><span data-stu-id="b3b78-102">Init Method</span></span>
<span data-ttu-id="b3b78-103">Prépare les objets qui implémentent l' [interface IALink](ialink-interface.md) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b3b78-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3b78-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3b78-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b3b78-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="b3b78-106">[IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) pointeur d’interface vers le distributeur de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b3b78-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="b3b78-107">Pointeur d' [interface IMetaDataError](../metadata/imetadataerror-interface.md) vers une interface de gestion des erreurs facultative.</span><span class="sxs-lookup"><span data-stu-id="b3b78-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3b78-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b3b78-108">Return Value</span></span>  
 <span data-ttu-id="b3b78-109">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="b3b78-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b78-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b3b78-110">Requirements</span></span>  
 <span data-ttu-id="b3b78-111">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="b3b78-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b78-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3b78-112">See also</span></span>

- [<span data-ttu-id="b3b78-113">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="b3b78-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b3b78-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="b3b78-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b3b78-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="b3b78-115">ALink API</span></span>](index.md)
