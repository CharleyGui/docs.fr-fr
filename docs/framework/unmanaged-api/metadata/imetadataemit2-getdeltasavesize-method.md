---
title: IMetaDataEmit2::GetDeltaSaveSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 24fe8fd65b36e133b767cd07c8602aa1ea7b9dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493099"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="a66c6-102">IMetaDataEmit2::GetDeltaSaveSize, méthode</span><span class="sxs-lookup"><span data-stu-id="a66c6-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="a66c6-103">Obtient une valeur indiquant toute modification de la taille des métadonnées résultant de la session de modification et de continuation actuelle.</span><span class="sxs-lookup"><span data-stu-id="a66c6-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a66c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a66c6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a66c6-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="a66c6-106">dans L’une des valeurs [CorSaveSize,](corsavesize-enumeration.md) , indiquant le niveau de précision souhaité.</span><span class="sxs-lookup"><span data-stu-id="a66c6-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="a66c6-107">Pour la version .NET Framework 2,0, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="a66c6-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="a66c6-108">à Modification de la taille des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a66c6-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a66c6-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a66c6-109">Requirements</span></span>  
 <span data-ttu-id="a66c6-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a66c6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a66c6-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a66c6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a66c6-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a66c6-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a66c6-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a66c6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66c6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a66c6-114">See also</span></span>

- [<span data-ttu-id="a66c6-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a66c6-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="a66c6-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a66c6-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
