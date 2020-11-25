---
title: IMetaDataImport::EnumProperties, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
ms.openlocfilehash: 24ee37a36e34c74258e1c750ba424640c0496f0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728249"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="c2fbb-102">IMetaDataImport::EnumProperties, méthode</span><span class="sxs-lookup"><span data-stu-id="c2fbb-102">IMetaDataImport::EnumProperties Method</span></span>

<span data-ttu-id="c2fbb-103">Énumère les jetons PropertyDef représentant les propriétés du type référencé par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2fbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2fbb-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2fbb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c2fbb-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c2fbb-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c2fbb-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="c2fbb-108">dans Jeton TypeDef représentant le type avec des propriétés à énumérer.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="c2fbb-109">à Tableau utilisé pour stocker les jetons PropertyDef.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c2fbb-110">[in] Taille maximale du tableau `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="c2fbb-111">à Nombre de jetons PropertyDef retournés dans `rProperties` .</span><span class="sxs-lookup"><span data-stu-id="c2fbb-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2fbb-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c2fbb-112">Return Value</span></span>  
  
|<span data-ttu-id="c2fbb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2fbb-113">HRESULT</span></span>|<span data-ttu-id="c2fbb-114">Description</span><span class="sxs-lookup"><span data-stu-id="c2fbb-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c2fbb-115">`EnumProperties` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c2fbb-116">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="c2fbb-117">Dans ce cas, `pcProperties` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="c2fbb-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2fbb-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c2fbb-118">Requirements</span></span>  

 <span data-ttu-id="c2fbb-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2fbb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2fbb-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c2fbb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2fbb-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2fbb-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2fbb-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2fbb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2fbb-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2fbb-123">See also</span></span>

- [<span data-ttu-id="c2fbb-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c2fbb-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c2fbb-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c2fbb-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
