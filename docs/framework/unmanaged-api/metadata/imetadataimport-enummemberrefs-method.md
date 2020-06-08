---
title: IMetaDataImport::EnumMemberRefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: 68cdefe7ab362b26bbf060fa46766068eb0d7094
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503755"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="ed394-102">IMetaDataImport::EnumMemberRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="ed394-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="ed394-103">Énumère les jetons MemberRef représentant les membres du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="ed394-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed394-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed394-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed394-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ed394-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ed394-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="ed394-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="ed394-107">dans Jeton TypeDef, TypeRef, MethodDef ou ModuleRef pour le type dont les membres doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="ed394-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="ed394-108">à Tableau utilisé pour stocker les jetons MemberRef.</span><span class="sxs-lookup"><span data-stu-id="ed394-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ed394-109">[in] Taille maximale du tableau `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="ed394-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ed394-110">à Nombre réel de jetons MemberRef retournés dans `rMemberRefs` .</span><span class="sxs-lookup"><span data-stu-id="ed394-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed394-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ed394-111">Return Value</span></span>  
  
|<span data-ttu-id="ed394-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed394-112">HRESULT</span></span>|<span data-ttu-id="ed394-113">Description</span><span class="sxs-lookup"><span data-stu-id="ed394-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ed394-114">`EnumMemberRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ed394-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ed394-115">Il n’y a aucun Jeton MemberRef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="ed394-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="ed394-116">Dans ce cas, `pcTokens` est à zéro.</span><span class="sxs-lookup"><span data-stu-id="ed394-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed394-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ed394-117">Requirements</span></span>  
 <span data-ttu-id="ed394-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed394-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed394-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ed394-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed394-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed394-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed394-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed394-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed394-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed394-122">See also</span></span>

- [<span data-ttu-id="ed394-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ed394-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ed394-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="ed394-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
