---
title: IMetaDataEmit::SetFieldRVA, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: 8468b0e7faa520fe2d27e17674af5503871d3b62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730381"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="75b9f-102">IMetaDataEmit::SetFieldRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="75b9f-102">IMetaDataEmit::SetFieldRVA Method</span></span>

<span data-ttu-id="75b9f-103">Définit une valeur de variable globale pour l’adresse virtuelle relative du champ référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="75b9f-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75b9f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75b9f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="75b9f-105">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="75b9f-106">dans Jeton pour le champ cible.</span><span class="sxs-lookup"><span data-stu-id="75b9f-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="75b9f-107">dans Adresse d’un code ou d’une zone de données.</span><span class="sxs-lookup"><span data-stu-id="75b9f-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75b9f-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="75b9f-108">Requirements</span></span>  

 <span data-ttu-id="75b9f-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75b9f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75b9f-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="75b9f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75b9f-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75b9f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75b9f-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75b9f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b9f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75b9f-113">See also</span></span>

- [<span data-ttu-id="75b9f-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="75b9f-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="75b9f-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="75b9f-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
