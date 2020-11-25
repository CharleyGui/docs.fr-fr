---
title: IMetaDataImport::EnumMethods, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 00726b7e74bdedc658886cccbc4329eaf3ae76d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696802"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="a39ce-102">IMetaDataImport::EnumMethods, méthode</span><span class="sxs-lookup"><span data-stu-id="a39ce-102">IMetaDataImport::EnumMethods Method</span></span>

<span data-ttu-id="a39ce-103">Énumère les jetons MethodDef représentant les méthodes du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="a39ce-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a39ce-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a39ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a39ce-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="a39ce-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a39ce-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a39ce-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="a39ce-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="a39ce-108">dans Jeton TypeDef représentant le type avec les méthodes à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a39ce-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="a39ce-109">à Tableau pour stocker les jetons MethodDef.</span><span class="sxs-lookup"><span data-stu-id="a39ce-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a39ce-110">dans Taille maximale du `rMethods` tableau MethodDef.</span><span class="sxs-lookup"><span data-stu-id="a39ce-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a39ce-111">à Nombre de jetons MethodDef retournés dans `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="a39ce-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a39ce-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a39ce-112">Return Value</span></span>  
  
|<span data-ttu-id="a39ce-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a39ce-113">HRESULT</span></span>|<span data-ttu-id="a39ce-114">Description</span><span class="sxs-lookup"><span data-stu-id="a39ce-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a39ce-115">`EnumMethods` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a39ce-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a39ce-116">Il n’y a aucun jeton MethodDef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a39ce-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="a39ce-117">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="a39ce-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a39ce-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a39ce-118">Requirements</span></span>  

 <span data-ttu-id="a39ce-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a39ce-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a39ce-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a39ce-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a39ce-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a39ce-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a39ce-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a39ce-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39ce-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a39ce-123">See also</span></span>

- [<span data-ttu-id="a39ce-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="a39ce-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a39ce-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="a39ce-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
