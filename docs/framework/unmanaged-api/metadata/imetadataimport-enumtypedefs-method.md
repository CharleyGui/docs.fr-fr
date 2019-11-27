---
title: IMetaDataImport::EnumTypeDefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449996"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="2a074-102">IMetaDataImport::EnumTypeDefs, méthode</span><span class="sxs-lookup"><span data-stu-id="2a074-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="2a074-103">Énumère les jetons TypeDef représentant tous les types au sein la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="2a074-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a074-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a074-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a074-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2a074-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2a074-106">à Pointeur vers le nouvel énumérateur.</span><span class="sxs-lookup"><span data-stu-id="2a074-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="2a074-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="2a074-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="2a074-108">dans Tableau utilisé pour stocker les jetons TypeDef.</span><span class="sxs-lookup"><span data-stu-id="2a074-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2a074-109">[in] Taille maximale du tableau `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="2a074-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="2a074-110">à Nombre de jetons TypeDef retournés dans `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="2a074-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a074-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2a074-111">Return Value</span></span>  
  
|<span data-ttu-id="2a074-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a074-112">HRESULT</span></span>|<span data-ttu-id="2a074-113">Description</span><span class="sxs-lookup"><span data-stu-id="2a074-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2a074-114">`EnumTypeDefs` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2a074-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2a074-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="2a074-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2a074-116">Dans ce cas, `pcTypeDefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="2a074-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a074-117">Notes</span><span class="sxs-lookup"><span data-stu-id="2a074-117">Remarks</span></span>  
 <span data-ttu-id="2a074-118">Le jeton TypeDef représente un type tel qu’une classe ou une interface, ainsi qu’un type ajouté via un mécanisme d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="2a074-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a074-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2a074-119">Requirements</span></span>  
 <span data-ttu-id="2a074-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a074-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a074-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2a074-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a074-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2a074-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a074-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a074-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a074-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a074-124">See also</span></span>

- [<span data-ttu-id="2a074-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="2a074-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2a074-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="2a074-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
