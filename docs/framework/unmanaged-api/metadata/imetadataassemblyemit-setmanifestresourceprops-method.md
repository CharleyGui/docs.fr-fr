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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d080a3077df2cb4ad57ef463b5e02a3a28d8429d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779410"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="abab6-102">IMetaDataAssemblyEmit::SetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="abab6-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="abab6-103">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="abab6-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abab6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abab6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abab6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="abab6-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="abab6-106">[in] Le jeton qui spécifie la `ManifestResource` structure des métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="abab6-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="abab6-107">[in] Le jeton, de type `File` ou `AssemblyRef`, qui mappe au fournisseur de ressources.</span><span class="sxs-lookup"><span data-stu-id="abab6-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="abab6-108">[in] Offset au début de la ressource dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="abab6-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="abab6-109">[in] Une combinaison au niveau du bit des valeurs d’indicateurs qui spécifient les attributs de la ressource.</span><span class="sxs-lookup"><span data-stu-id="abab6-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abab6-110">Notes</span><span class="sxs-lookup"><span data-stu-id="abab6-110">Remarks</span></span>  
 <span data-ttu-id="abab6-111">Pour créer un `ManifestResource` structure des métadonnées, utilisez le [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="abab6-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abab6-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="abab6-112">Requirements</span></span>  
 <span data-ttu-id="abab6-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abab6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abab6-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="abab6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abab6-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abab6-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="abab6-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abab6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abab6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abab6-117">See also</span></span>

- [<span data-ttu-id="abab6-118">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="abab6-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
