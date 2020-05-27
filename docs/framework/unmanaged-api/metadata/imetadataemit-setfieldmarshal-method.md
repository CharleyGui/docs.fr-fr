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
ms.openlocfilehash: d0066c6590a9e0cf278e036111c2739f7cfaf679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003904"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="9b302-102">IMetaDataEmit::SetFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="9b302-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="9b302-103">Définit les informations de marshaling PInvoke pour le champ, le retour de méthode ou le paramètre de méthode référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b302-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b302-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b302-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b302-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b302-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9b302-106">dans Jeton pour l’élément de données cibles.</span><span class="sxs-lookup"><span data-stu-id="9b302-106">[in] The token for target data item.</span></span> <span data-ttu-id="9b302-107">Il s’agit soit d’un jeton, soit d’un `mdFieldDef` `mdParamDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="9b302-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="9b302-108">dans Signature pour le type non managé.</span><span class="sxs-lookup"><span data-stu-id="9b302-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="9b302-109">dans Nombre d’octets dans `pvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="9b302-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b302-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9b302-110">Requirements</span></span>  
 <span data-ttu-id="9b302-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b302-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b302-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9b302-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b302-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b302-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b302-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b302-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b302-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b302-115">See also</span></span>

- [<span data-ttu-id="9b302-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9b302-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9b302-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="9b302-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
