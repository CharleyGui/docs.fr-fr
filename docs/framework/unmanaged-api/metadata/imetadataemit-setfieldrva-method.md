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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93ca394eb877a86e4242d5f9f18eb26f5628db7e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751078"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="f3087-102">IMetaDataEmit::SetFieldRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="f3087-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="f3087-103">Définit une valeur de variable globale pour l’adresse virtuelle relative du champ référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="f3087-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3087-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3087-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3087-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f3087-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="f3087-106">[in] Le jeton pour le champ cible.</span><span class="sxs-lookup"><span data-stu-id="f3087-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="f3087-107">[in] L’adresse d’une zone de code ou de données.</span><span class="sxs-lookup"><span data-stu-id="f3087-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3087-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f3087-108">Requirements</span></span>  
 <span data-ttu-id="f3087-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3087-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3087-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3087-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3087-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3087-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3087-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3087-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3087-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3087-113">See also</span></span>

- [<span data-ttu-id="f3087-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f3087-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f3087-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f3087-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
