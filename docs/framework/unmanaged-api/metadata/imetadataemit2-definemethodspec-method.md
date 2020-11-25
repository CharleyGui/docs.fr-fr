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
ms.openlocfilehash: 817b3a18b047bfca1f3a7c7099920a12e6253f58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712831"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="e85e7-102">IMetaDataEmit2::DefineMethodSpec, méthode</span><span class="sxs-lookup"><span data-stu-id="e85e7-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>

<span data-ttu-id="e85e7-103">Crée une instance générique d’une méthode et obtient un jeton pour la définition.</span><span class="sxs-lookup"><span data-stu-id="e85e7-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e85e7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e85e7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e85e7-105">Parameters</span></span>  

 `tkParent`  
 <span data-ttu-id="e85e7-106">dans Jeton pour la méthode pour laquelle créer l’instance générique.</span><span class="sxs-lookup"><span data-stu-id="e85e7-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="e85e7-107">Le jeton doit être de type `mdMethodDef` ou `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="e85e7-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e85e7-108">dans Pointeur vers la signature COM+ binaire de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e85e7-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="e85e7-109">dans Taille, en octets, de `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="e85e7-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="e85e7-110">à Jeton pour la définition de signature de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e85e7-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e85e7-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e85e7-111">Requirements</span></span>  

 <span data-ttu-id="e85e7-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e85e7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e85e7-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e85e7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e85e7-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e85e7-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e85e7-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e85e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85e7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e85e7-116">See also</span></span>

- [<span data-ttu-id="e85e7-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e85e7-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="e85e7-118">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e85e7-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
