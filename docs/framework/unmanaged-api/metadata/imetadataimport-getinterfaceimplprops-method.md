---
title: IMetaDataImport::GetInterfaceImplProps, méthode
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175380"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="7888c-102">IMetaDataImport::GetInterfaceImplProps, méthode</span><span class="sxs-lookup"><span data-stu-id="7888c-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="7888c-103">Obtient un pointeur pour les jetons <xref:System.Type> de métadonnées pour le qui implémente la méthode spécifiée, et pour l’interface qui déclare cette méthode.</span><span class="sxs-lookup"><span data-stu-id="7888c-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="7888c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7888c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7888c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7888c-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="7888c-106">[dans] Le jeton des métadonnées représentant la méthode pour retourner les jetons de classe et d’interface pour.</span><span class="sxs-lookup"><span data-stu-id="7888c-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="7888c-107">[out] Le jeton des métadonnées représentant la classe qui met en œuvre la méthode.</span><span class="sxs-lookup"><span data-stu-id="7888c-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="7888c-108">[out] Le jeton des métadonnées représentant l’interface qui définit la méthode mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="7888c-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="7888c-109">Notes </span><span class="sxs-lookup"><span data-stu-id="7888c-109">Remarks</span></span>

 <span data-ttu-id="7888c-110">Vous obtenez la `iImpl` valeur pour appeler la méthode [EnumInterfaceImpls.](imetadataimport-enuminterfaceimpls-method.md)</span><span class="sxs-lookup"><span data-stu-id="7888c-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="7888c-111">Supposons, par exemple, `mdTypeDef` qu’une classe a une valeur symbolique de 0x02000007 et qu’elle implémente trois interfaces dont les types ont des jetons :</span><span class="sxs-lookup"><span data-stu-id="7888c-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="7888c-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="7888c-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="7888c-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="7888c-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="7888c-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="7888c-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="7888c-115">Conceptuellement, ces informations sont stockées dans une table de mise en œuvre d’interface comme :</span><span class="sxs-lookup"><span data-stu-id="7888c-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="7888c-116">Numéro de rangée</span><span class="sxs-lookup"><span data-stu-id="7888c-116">Row number</span></span> | <span data-ttu-id="7888c-117">Jeton de classe</span><span class="sxs-lookup"><span data-stu-id="7888c-117">Class token</span></span> | <span data-ttu-id="7888c-118">Jeton d’interface</span><span class="sxs-lookup"><span data-stu-id="7888c-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="7888c-119">4</span><span class="sxs-lookup"><span data-stu-id="7888c-119">4</span></span>          |             |                 |
| <span data-ttu-id="7888c-120">5</span><span class="sxs-lookup"><span data-stu-id="7888c-120">5</span></span>          | <span data-ttu-id="7888c-121">02000007</span><span class="sxs-lookup"><span data-stu-id="7888c-121">02000007</span></span>    | <span data-ttu-id="7888c-122">02000003</span><span class="sxs-lookup"><span data-stu-id="7888c-122">02000003</span></span>        |
| <span data-ttu-id="7888c-123">6</span><span class="sxs-lookup"><span data-stu-id="7888c-123">6</span></span>          | <span data-ttu-id="7888c-124">02000007</span><span class="sxs-lookup"><span data-stu-id="7888c-124">02000007</span></span>    | <span data-ttu-id="7888c-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="7888c-125">0100000A</span></span>        |
| <span data-ttu-id="7888c-126">7</span><span class="sxs-lookup"><span data-stu-id="7888c-126">7</span></span>          |             |                 |
| <span data-ttu-id="7888c-127">8</span><span class="sxs-lookup"><span data-stu-id="7888c-127">8</span></span>          | <span data-ttu-id="7888c-128">02000007</span><span class="sxs-lookup"><span data-stu-id="7888c-128">02000007</span></span>    | <span data-ttu-id="7888c-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="7888c-129">0200001C</span></span>        |

<span data-ttu-id="7888c-130">Rappelons que le jeton est une valeur de 4 byte :</span><span class="sxs-lookup"><span data-stu-id="7888c-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="7888c-131">Les 3 octets inférieurs détiennent le numéro de rangée, ou RID.</span><span class="sxs-lookup"><span data-stu-id="7888c-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="7888c-132">Le haut byte détient le type symbolique - `mdtInterfaceImpl`0x09 pour .</span><span class="sxs-lookup"><span data-stu-id="7888c-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="7888c-133">`GetInterfaceImplProps`retourne l’information détenue dans la rangée `iImpl` dont vous fournissez le jeton dans l’argument.</span><span class="sxs-lookup"><span data-stu-id="7888c-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="7888c-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7888c-134">Requirements</span></span>  
 <span data-ttu-id="7888c-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7888c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7888c-136">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="7888c-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7888c-137">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7888c-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7888c-138">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7888c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7888c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7888c-139">See also</span></span>

- [<span data-ttu-id="7888c-140">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="7888c-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7888c-141">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="7888c-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
