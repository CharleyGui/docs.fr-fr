---
title: IMetaDataEmit::SetFieldMarshal, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: cdbcdb9359d295ad9bed2050ed36499feba74d9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442275"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="c0da3-102">IMetaDataEmit::SetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="c0da3-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="c0da3-103">Définit les informations de marshaling PInvoke pour le champ, le retour de méthode ou le paramètre de méthode référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="c0da3-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0da3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0da3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0da3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0da3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c0da3-106">dans Jeton pour l’élément de données cibles.</span><span class="sxs-lookup"><span data-stu-id="c0da3-106">[in] The token for target data item.</span></span> <span data-ttu-id="c0da3-107">Il s’agit soit d’un `mdFieldDef`, soit d’un jeton `mdParamDef`.</span><span class="sxs-lookup"><span data-stu-id="c0da3-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="c0da3-108">dans Signature pour le type non managé.</span><span class="sxs-lookup"><span data-stu-id="c0da3-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="c0da3-109">dans Nombre d’octets dans `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="c0da3-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0da3-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c0da3-110">Requirements</span></span>  
 <span data-ttu-id="c0da3-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0da3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0da3-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c0da3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0da3-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c0da3-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0da3-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0da3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0da3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0da3-115">See also</span></span>

- [<span data-ttu-id="c0da3-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="c0da3-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c0da3-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="c0da3-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
