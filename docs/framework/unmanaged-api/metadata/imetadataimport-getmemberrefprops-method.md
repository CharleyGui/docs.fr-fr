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
ms.openlocfilehash: 1d6d66ea62cbf679f722f830b3638455001aedd6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437491"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="33717-102">IMetaDataImport::GetMemberRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="33717-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="33717-103">Obtient les métadonnées associées au membre référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="33717-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33717-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33717-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="33717-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="33717-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="33717-106">dans Jeton MemberRef pour lequel retourner les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="33717-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="33717-107">à Un jeton TypeDef ou TypeRef, ou TypeSpec qui représente la classe qui déclare le membre, ou un jeton ModuleRef qui représente la classe de module qui déclare le membre, ou un MethodDef qui représente le membre.</span><span class="sxs-lookup"><span data-stu-id="33717-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="33717-108">à Mémoire tampon de chaîne pour le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="33717-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="33717-109">dans Taille demandée en caractères larges de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="33717-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="33717-110">à Taille retournée en caractères larges de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="33717-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="33717-111">à Pointeur vers la signature de métadonnées binaires pour le membre.</span><span class="sxs-lookup"><span data-stu-id="33717-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="33717-112">à Taille en octets de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="33717-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33717-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="33717-113">Requirements</span></span>  
 <span data-ttu-id="33717-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33717-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33717-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="33717-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33717-116">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="33717-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33717-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33717-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33717-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33717-118">See also</span></span>

- [<span data-ttu-id="33717-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="33717-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="33717-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="33717-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
