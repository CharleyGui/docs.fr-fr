---
title: IMetaDataImport::FindTypeRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8159b5245598993a2075fb402b280f9ab4cb2cfa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782460"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="ccb92-102">IMetaDataImport::FindTypeRef, méthode</span><span class="sxs-lookup"><span data-stu-id="ccb92-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="ccb92-103">Obtient un pointeur vers le jeton TypeRef pour la <xref:System.Type> référence qui se trouve dans la portée spécifiée et qui porte le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="ccb92-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccb92-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccb92-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ccb92-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="ccb92-106">[in] Un jeton ModuleRef, AssemblyRef ou TypeRef qui spécifie le module, un assembly ou un type, respectivement, dans lequel la référence de type est défini.</span><span class="sxs-lookup"><span data-stu-id="ccb92-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="ccb92-107">[in] Le nom de la référence de type à rechercher.</span><span class="sxs-lookup"><span data-stu-id="ccb92-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="ccb92-108">[out] Pointeur vers le jeton TypeRef correspondant.</span><span class="sxs-lookup"><span data-stu-id="ccb92-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccb92-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ccb92-109">Requirements</span></span>  
 <span data-ttu-id="ccb92-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccb92-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccb92-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ccb92-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccb92-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ccb92-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccb92-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccb92-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb92-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccb92-114">See also</span></span>

- [<span data-ttu-id="ccb92-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ccb92-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ccb92-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="ccb92-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
