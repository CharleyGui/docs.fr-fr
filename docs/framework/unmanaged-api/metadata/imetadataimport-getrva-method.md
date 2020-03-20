---
title: IMetaDataImport::GetRVA, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177215"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="36bfc-102">IMetaDataImport::GetRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="36bfc-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="36bfc-103">Obtient l’adresse virtuelle relative (RVA) et les drapeaux de mise en œuvre de la méthode ou du champ représentés par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="36bfc-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36bfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36bfc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36bfc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="36bfc-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="36bfc-106">[dans] Un jeton de métadonnées MethodDef ou FieldDef qui représente l’objet de code pour retourner le RVA.</span><span class="sxs-lookup"><span data-stu-id="36bfc-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="36bfc-107">Si le jeton est un FieldDef, le champ doit être une variable globale.</span><span class="sxs-lookup"><span data-stu-id="36bfc-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="36bfc-108">[out] Un pointeur vers l’adresse virtuelle relative de l’objet de code représenté par le jeton.</span><span class="sxs-lookup"><span data-stu-id="36bfc-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="36bfc-109">[out] Un pointeur pour les drapeaux de mise en œuvre pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="36bfc-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="36bfc-110">Cette valeur est un peumask de l’énumération [CorMethodImpl.](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="36bfc-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="36bfc-111">La valeur `pdwImplFlags` de est `tk` valide seulement si est un jeton MethodDef.</span><span class="sxs-lookup"><span data-stu-id="36bfc-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36bfc-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="36bfc-112">Requirements</span></span>  
 <span data-ttu-id="36bfc-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36bfc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36bfc-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="36bfc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36bfc-115">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36bfc-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36bfc-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36bfc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bfc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36bfc-117">See also</span></span>

- [<span data-ttu-id="36bfc-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="36bfc-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="36bfc-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="36bfc-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
