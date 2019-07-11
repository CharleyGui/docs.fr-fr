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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a4305b94d785a764671a2d73f43facefd0da0e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782374"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="ed38d-102">IMetaDataImport::GetInterfaceImplProps, méthode</span><span class="sxs-lookup"><span data-stu-id="ed38d-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="ed38d-103">Obtient un pointeur vers les jetons de métadonnées pour le <xref:System.Type> qui implémente la méthode spécifiée, et pour l’interface qui déclare cette méthode.</span><span class="sxs-lookup"><span data-stu-id="ed38d-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ed38d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed38d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed38d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ed38d-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="ed38d-106">[in] Représentant la méthode pour renvoyer les jetons de classe et d’interface pour le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ed38d-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ed38d-107">[out] Le jeton de métadonnées représentant la classe qui implémente la méthode.</span><span class="sxs-lookup"><span data-stu-id="ed38d-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="ed38d-108">[out] Le jeton de métadonnées qui représente l’interface qui définit la méthode implémentée.</span><span class="sxs-lookup"><span data-stu-id="ed38d-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="ed38d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ed38d-109">Remarks</span></span>

 <span data-ttu-id="ed38d-110">Vous obtenez la valeur de `iImpl` en appelant le [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ed38d-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="ed38d-111">Par exemple, supposons qu’une classe a un `mdTypeDef` jeton la valeur de 0 x 02000007 et qu’elle implémente trois interfaces dont les types ont des jetons :</span><span class="sxs-lookup"><span data-stu-id="ed38d-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="ed38d-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="ed38d-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="ed38d-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="ed38d-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="ed38d-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="ed38d-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="ed38d-115">Conceptuellement, ces informations sont stockées dans une table de mise en œuvre d’interface en tant que :</span><span class="sxs-lookup"><span data-stu-id="ed38d-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="ed38d-116">Numéro de ligne</span><span class="sxs-lookup"><span data-stu-id="ed38d-116">Row number</span></span> | <span data-ttu-id="ed38d-117">Jeton de classe</span><span class="sxs-lookup"><span data-stu-id="ed38d-117">Class token</span></span> | <span data-ttu-id="ed38d-118">Jeton de l’interface</span><span class="sxs-lookup"><span data-stu-id="ed38d-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="ed38d-119">4</span><span class="sxs-lookup"><span data-stu-id="ed38d-119">4</span></span>          |             |                 |
| <span data-ttu-id="ed38d-120">5\.</span><span class="sxs-lookup"><span data-stu-id="ed38d-120">5</span></span>          | <span data-ttu-id="ed38d-121">02000007</span><span class="sxs-lookup"><span data-stu-id="ed38d-121">02000007</span></span>    | <span data-ttu-id="ed38d-122">02000003</span><span class="sxs-lookup"><span data-stu-id="ed38d-122">02000003</span></span>        |
| <span data-ttu-id="ed38d-123">6\.</span><span class="sxs-lookup"><span data-stu-id="ed38d-123">6</span></span>          | <span data-ttu-id="ed38d-124">02000007</span><span class="sxs-lookup"><span data-stu-id="ed38d-124">02000007</span></span>    | <span data-ttu-id="ed38d-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="ed38d-125">0100000A</span></span>        |
| <span data-ttu-id="ed38d-126">7</span><span class="sxs-lookup"><span data-stu-id="ed38d-126">7</span></span>          |             |                 |
| <span data-ttu-id="ed38d-127">8</span><span class="sxs-lookup"><span data-stu-id="ed38d-127">8</span></span>          | <span data-ttu-id="ed38d-128">02000007</span><span class="sxs-lookup"><span data-stu-id="ed38d-128">02000007</span></span>    | <span data-ttu-id="ed38d-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="ed38d-129">0200001C</span></span>        |

<span data-ttu-id="ed38d-130">Rappelez-vous, le jeton est une valeur de 4 octets :</span><span class="sxs-lookup"><span data-stu-id="ed38d-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="ed38d-131">Les 3 octets contenant le nombre de lignes ou RID.</span><span class="sxs-lookup"><span data-stu-id="ed38d-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="ed38d-132">L’octet de poids fort conserve le type de jeton : 0 x 09 pour `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="ed38d-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="ed38d-133">`GetInterfaceImplProps` Retourne les informations contenues dans la ligne dont le jeton que vous fournissez dans le `iImpl` argument.</span><span class="sxs-lookup"><span data-stu-id="ed38d-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="ed38d-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ed38d-134">Requirements</span></span>  
 <span data-ttu-id="ed38d-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed38d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed38d-136">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ed38d-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed38d-137">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed38d-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed38d-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed38d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed38d-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed38d-139">See also</span></span>

- [<span data-ttu-id="ed38d-140">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ed38d-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ed38d-141">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="ed38d-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
