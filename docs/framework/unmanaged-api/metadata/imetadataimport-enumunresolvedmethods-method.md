---
title: IMetaDataImport::EnumUnresolvedMethods, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: 6b5e7bbe2303a200d7829fea12e228a513595f97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716549"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="e8210-102">IMetaDataImport::EnumUnresolvedMethods, méthode</span><span class="sxs-lookup"><span data-stu-id="e8210-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>

<span data-ttu-id="e8210-103">Énumère les jetons MemberDef représentant les méthodes non résolues dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="e8210-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8210-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8210-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8210-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8210-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="e8210-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e8210-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e8210-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e8210-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="e8210-108">à Tableau utilisé pour stocker les jetons MemberDef.</span><span class="sxs-lookup"><span data-stu-id="e8210-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e8210-109">[in] Taille maximale du tableau `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="e8210-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e8210-110">à Nombre de jetons MemberDef retournés dans `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="e8210-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8210-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e8210-111">Return Value</span></span>  
  
|<span data-ttu-id="e8210-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8210-112">HRESULT</span></span>|<span data-ttu-id="e8210-113">Description</span><span class="sxs-lookup"><span data-stu-id="e8210-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e8210-114">`EnumUnresolvedMethods` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e8210-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e8210-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="e8210-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e8210-116">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="e8210-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8210-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8210-117">Remarks</span></span>  

 <span data-ttu-id="e8210-118">Une méthode non résolue est une méthode qui a été déclarée mais qui n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="e8210-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="e8210-119">Une méthode est incluse dans l’énumération si la méthode est marquée `miForwardRef` et si `mdPinvokeImpl` ou a la `miRuntime` valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="e8210-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="e8210-120">En d’autres termes, une méthode non résolue est une méthode de classe marquée `miForwardRef` mais qui n’est pas implémentée dans du code non managé (atteinte via PInvoke), ni implémentée en interne par le runtime lui-même</span><span class="sxs-lookup"><span data-stu-id="e8210-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="e8210-121">L’énumération exclut toutes les méthodes définies au niveau de la portée du module (globales) ou dans les interfaces ou les classes abstraites.</span><span class="sxs-lookup"><span data-stu-id="e8210-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8210-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e8210-122">Requirements</span></span>  

 <span data-ttu-id="e8210-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8210-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8210-124">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e8210-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8210-125">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8210-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8210-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8210-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8210-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8210-127">See also</span></span>

- [<span data-ttu-id="e8210-128">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="e8210-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e8210-129">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="e8210-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
