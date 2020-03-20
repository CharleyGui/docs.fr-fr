---
title: IMetaDataAssemblyEmit::SetManifestResourceProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
ms.openlocfilehash: 9370b27fd385b0223b354365d64aa57048f4ec69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177843"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="36abd-102">IMetaDataAssemblyEmit::SetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="36abd-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="36abd-103">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="36abd-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36abd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36abd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36abd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="36abd-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="36abd-106">[dans] Le jeton qui spécifie la `ManifestResource` structure des métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="36abd-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="36abd-107">[dans] Le jeton, `File` de `AssemblyRef`type ou , qui cartes au fournisseur de ressources.</span><span class="sxs-lookup"><span data-stu-id="36abd-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="36abd-108">[dans] La compensation au début de la ressource dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="36abd-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="36abd-109">[dans] Une combinaison peu sage de valeurs de drapeau qui spécifient les attributs de la ressource.</span><span class="sxs-lookup"><span data-stu-id="36abd-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36abd-110">Notes </span><span class="sxs-lookup"><span data-stu-id="36abd-110">Remarks</span></span>  
 <span data-ttu-id="36abd-111">Pour créer `ManifestResource` une structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit::DefineManifestResource.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)</span><span class="sxs-lookup"><span data-stu-id="36abd-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36abd-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="36abd-112">Requirements</span></span>  
 <span data-ttu-id="36abd-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36abd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36abd-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="36abd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36abd-115">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36abd-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36abd-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36abd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36abd-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36abd-117">See also</span></span>

- [<span data-ttu-id="36abd-118">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="36abd-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
