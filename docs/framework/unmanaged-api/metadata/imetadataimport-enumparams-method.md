---
title: IMetaDataImport::EnumParams, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: e5fa3647c86d97730e7ad6a2576dd34af75251d6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433961"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="749ed-102">IMetaDataImport::EnumParams, méthode</span><span class="sxs-lookup"><span data-stu-id="749ed-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="749ed-103">Énumère les jetons ParamDef représentant les paramètres de la méthode référencée par le jeton MethodDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="749ed-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="749ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="749ed-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="749ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="749ed-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="749ed-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="749ed-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="749ed-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="749ed-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="749ed-108">dans Jeton MethodDef représentant la méthode avec les paramètres à énumérer.</span><span class="sxs-lookup"><span data-stu-id="749ed-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="749ed-109">à Tableau utilisé pour stocker les jetons ParamDef.</span><span class="sxs-lookup"><span data-stu-id="749ed-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="749ed-110">[in] Taille maximale du tableau `rParams`.</span><span class="sxs-lookup"><span data-stu-id="749ed-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="749ed-111">à Nombre de jetons ParamDef retournés dans `rParams`.</span><span class="sxs-lookup"><span data-stu-id="749ed-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="749ed-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="749ed-112">Return Value</span></span>  
  
|<span data-ttu-id="749ed-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="749ed-113">HRESULT</span></span>|<span data-ttu-id="749ed-114">Description</span><span class="sxs-lookup"><span data-stu-id="749ed-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="749ed-115">`EnumParams` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="749ed-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="749ed-116">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="749ed-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="749ed-117">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="749ed-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="749ed-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="749ed-118">Requirements</span></span>  
 <span data-ttu-id="749ed-119">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="749ed-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="749ed-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="749ed-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="749ed-121">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="749ed-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="749ed-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="749ed-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="749ed-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="749ed-123">See also</span></span>

- [<span data-ttu-id="749ed-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="749ed-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="749ed-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="749ed-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
