---
title: IMetaDataImport::GetMemberRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fadc54d74ce6027bd021e148a14cb0c432eb41fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782340"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="27d01-102">IMetaDataImport::GetMemberRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="27d01-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="27d01-103">Obtient les métadonnées associées au membre référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="27d01-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27d01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27d01-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27d01-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27d01-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="27d01-106">[in] Le jeton MemberRef pour retourner les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="27d01-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="27d01-107">[out] Jeton TypeDef ou TypeRef ou TypeSpec qui représente la classe qui déclare le membre, ou un jeton ModuleRef qui représente la classe de module qui déclare le membre, ou MethodDef qui représente le membre.</span><span class="sxs-lookup"><span data-stu-id="27d01-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="27d01-108">[out] Un mémoire tampon de chaîne pour le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="27d01-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="27d01-109">[in] La taille demandée en caractères larges de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="27d01-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="27d01-110">[out] La taille retournée en caractères larges de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="27d01-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="27d01-111">[out] Pointeur vers la signature de métadonnées binaires pour le membre.</span><span class="sxs-lookup"><span data-stu-id="27d01-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="27d01-112">[out] La taille en octets de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="27d01-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27d01-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="27d01-113">Requirements</span></span>  
 <span data-ttu-id="27d01-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27d01-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27d01-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="27d01-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27d01-116">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27d01-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27d01-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27d01-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d01-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27d01-118">See also</span></span>

- [<span data-ttu-id="27d01-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="27d01-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="27d01-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="27d01-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
