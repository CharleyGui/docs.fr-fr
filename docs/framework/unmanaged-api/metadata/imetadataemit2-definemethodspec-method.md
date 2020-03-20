---
title: IMetaDataEmit2::DefineMethodSpec, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: a5d9342b8bfe650106ccf9daf2a91dfbcd575446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175536"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="08777-102">IMetaDataEmit2::DefineMethodSpec, méthode</span><span class="sxs-lookup"><span data-stu-id="08777-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="08777-103">Crée un exemple générique d’une méthode, et obtient un jeton à la définition.</span><span class="sxs-lookup"><span data-stu-id="08777-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08777-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08777-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08777-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08777-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="08777-106">[dans] Un jeton pour la méthode de créer l’instance générique.</span><span class="sxs-lookup"><span data-stu-id="08777-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="08777-107">Le jeton doit `mdMethodDef` être `mdMemberRef`de type ou .</span><span class="sxs-lookup"><span data-stu-id="08777-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="08777-108">[dans] Un pointeur à la signature binaire COM DE la méthode.</span><span class="sxs-lookup"><span data-stu-id="08777-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="08777-109">[dans] La taille, dans les `pvSigBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="08777-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="08777-110">[out] Un jeton à la définition de signature des métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="08777-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08777-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="08777-111">Requirements</span></span>  
 <span data-ttu-id="08777-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08777-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08777-113">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="08777-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08777-114">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08777-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08777-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08777-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08777-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08777-116">See also</span></span>

- [<span data-ttu-id="08777-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="08777-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="08777-118">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="08777-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
