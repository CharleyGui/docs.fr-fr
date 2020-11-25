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
ms.openlocfilehash: c46a3bc34ba7efa760e50416e9a6c39779727813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708918"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="518fc-102">IMetaDataAssemblyEmit::SetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="518fc-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>

<span data-ttu-id="518fc-103">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="518fc-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="518fc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="518fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="518fc-105">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="518fc-106">dans Jeton qui spécifie la `ManifestResource` structure de métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="518fc-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="518fc-107">dans Jeton, de type `File` ou `AssemblyRef` , qui est mappé au fournisseur de ressources.</span><span class="sxs-lookup"><span data-stu-id="518fc-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="518fc-108">dans Offset au début de la ressource dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="518fc-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="518fc-109">dans Combinaison d’opérations de bits de valeurs d’indicateur qui spécifient les attributs de la ressource.</span><span class="sxs-lookup"><span data-stu-id="518fc-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="518fc-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="518fc-110">Remarks</span></span>  

 <span data-ttu-id="518fc-111">Pour créer une `ManifestResource` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efinemanifestresource](imetadataassemblyemit-definemanifestresource-method.md) .</span><span class="sxs-lookup"><span data-stu-id="518fc-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="518fc-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="518fc-112">Requirements</span></span>  

 <span data-ttu-id="518fc-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="518fc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="518fc-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="518fc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="518fc-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="518fc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="518fc-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="518fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="518fc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="518fc-117">See also</span></span>

- [<span data-ttu-id="518fc-118">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="518fc-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
