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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7700236efe7b031866867f5ed859ba71683a8a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782297"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="23cdb-102">IMetaDataImport2::GetMethodSpecProps, méthode</span><span class="sxs-lookup"><span data-stu-id="23cdb-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="23cdb-103">Obtient le jeton de signature de métadonnées de la méthode référencée par le MethodSpec spécifié.</span><span class="sxs-lookup"><span data-stu-id="23cdb-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23cdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23cdb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="23cdb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23cdb-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="23cdb-106">[in] Jeton MethodSpec qui représente l’instanciation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="23cdb-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="23cdb-107">[out] Pointeur vers le jeton MethodDef ou MethodRef qui représente la définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="23cdb-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="23cdb-108">[out] Pointeur vers la signature de métadonnées binaires de la méthode.</span><span class="sxs-lookup"><span data-stu-id="23cdb-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="23cdb-109">[out] La taille, en octets, de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="23cdb-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23cdb-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="23cdb-110">Requirements</span></span>  
 <span data-ttu-id="23cdb-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23cdb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23cdb-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23cdb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23cdb-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23cdb-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23cdb-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23cdb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23cdb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23cdb-115">See also</span></span>

- [<span data-ttu-id="23cdb-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="23cdb-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="23cdb-117">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="23cdb-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
