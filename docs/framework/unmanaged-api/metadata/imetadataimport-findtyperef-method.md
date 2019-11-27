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
ms.openlocfilehash: 21a69d120cc732ca6659f77abc9f8ea0c993271e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437790"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="c3409-102">IMetaDataImport::FindTypeRef, méthode</span><span class="sxs-lookup"><span data-stu-id="c3409-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="c3409-103">Obtient un pointeur vers le jeton TypeRef pour la référence <xref:System.Type> qui est dans la portée spécifiée et qui porte le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="c3409-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3409-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3409-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3409-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3409-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="c3409-106">dans Jeton ModuleRef, AssemblyRef ou TypeRef qui spécifie respectivement le module, l’assembly ou le type dans lequel la référence de type est définie.</span><span class="sxs-lookup"><span data-stu-id="c3409-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="c3409-107">dans Nom de la référence de type à rechercher.</span><span class="sxs-lookup"><span data-stu-id="c3409-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="c3409-108">à Pointeur vers le jeton TypeRef correspondant.</span><span class="sxs-lookup"><span data-stu-id="c3409-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3409-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c3409-109">Requirements</span></span>  
 <span data-ttu-id="c3409-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3409-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3409-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c3409-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3409-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3409-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3409-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3409-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3409-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3409-114">See also</span></span>

- [<span data-ttu-id="c3409-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c3409-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c3409-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c3409-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
