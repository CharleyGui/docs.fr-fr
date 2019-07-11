---
title: IMetaDataEmit::DefineMemberRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38e4928ad0f3560698cbecab81a11630d67e4db2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777614"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="3e7a4-102">IMetaDataEmit::DefineMemberRef, méthode</span><span class="sxs-lookup"><span data-stu-id="3e7a4-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="3e7a4-103">Définit une référence à un membre d’un module en dehors de la portée actuelle et obtient un jeton pour cette définition de référence.</span><span class="sxs-lookup"><span data-stu-id="3e7a4-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e7a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e7a4-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e7a4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e7a4-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="3e7a4-106">[in] Jeton pour la classe ou une interface, le membre cible si le membre n’est pas global ; Si le membre est global, le `mdModuleRef` jeton pour cet autre fichier.</span><span class="sxs-lookup"><span data-stu-id="3e7a4-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="3e7a4-107">[in] Le nom du membre cible.</span><span class="sxs-lookup"><span data-stu-id="3e7a4-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3e7a4-108">[in] La signature du membre cible.</span><span class="sxs-lookup"><span data-stu-id="3e7a4-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3e7a4-109">[in] Le nombre d’octets dans `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="3e7a4-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="3e7a4-110">[out] Le `mdMemberRef` jeton attribué.</span><span class="sxs-lookup"><span data-stu-id="3e7a4-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e7a4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3e7a4-111">Requirements</span></span>  
 <span data-ttu-id="3e7a4-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e7a4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e7a4-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3e7a4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e7a4-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e7a4-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e7a4-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e7a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e7a4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e7a4-116">See also</span></span>

- [<span data-ttu-id="3e7a4-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="3e7a4-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3e7a4-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="3e7a4-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
