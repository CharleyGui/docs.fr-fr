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
ms.openlocfilehash: 079d9245526ff7914d1cbd6a91f0f2d96a690af5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490443"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="191bf-102">IMetaDataImport2::GetMethodSpecProps, méthode</span><span class="sxs-lookup"><span data-stu-id="191bf-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="191bf-103">Obtient la signature de métadonnées de la méthode référencée par le jeton MethodSpec spécifié.</span><span class="sxs-lookup"><span data-stu-id="191bf-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="191bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="191bf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="191bf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="191bf-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="191bf-106">dans Jeton MethodSpec qui représente l’instanciation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="191bf-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="191bf-107">à Pointeur vers le jeton MethodDef ou MethodRef qui représente la définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="191bf-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="191bf-108">à Pointeur vers la signature de métadonnées binaires de la méthode.</span><span class="sxs-lookup"><span data-stu-id="191bf-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="191bf-109">à Taille, en octets, de `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="191bf-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="191bf-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="191bf-110">Requirements</span></span>  
 <span data-ttu-id="191bf-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="191bf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="191bf-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="191bf-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="191bf-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="191bf-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="191bf-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="191bf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191bf-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="191bf-115">See also</span></span>

- [<span data-ttu-id="191bf-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="191bf-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="191bf-117">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="191bf-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
