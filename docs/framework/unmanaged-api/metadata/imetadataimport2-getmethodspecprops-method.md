---
title: IMetaDataImport2::GetMethodSpecProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 0bfbfec930c193ea05a01bd5bd9f46d2ec6714b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175289"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="4c512-102">IMetaDataImport2::GetMethodSpecProps, méthode</span><span class="sxs-lookup"><span data-stu-id="4c512-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="4c512-103">Obtient la signature des métadonnées de la méthode référencée par le jeton MethodSpec spécifié.</span><span class="sxs-lookup"><span data-stu-id="4c512-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c512-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c512-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="4c512-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c512-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="4c512-106">[dans] Un jeton MethodSpec qui représente l’instantanéisation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4c512-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="4c512-107">[out] Un pointeur sur le jeton MethodDef ou MethodRef qui représente la définition de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4c512-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="4c512-108">[out] Un pointeur à la signature de métadonnées binaires de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4c512-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="4c512-109">[out] La taille, dans les `ppvSigBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="4c512-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c512-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4c512-110">Requirements</span></span>  
 <span data-ttu-id="4c512-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c512-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c512-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="4c512-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c512-113">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c512-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c512-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c512-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c512-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c512-115">See also</span></span>

- [<span data-ttu-id="4c512-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="4c512-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="4c512-117">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="4c512-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
