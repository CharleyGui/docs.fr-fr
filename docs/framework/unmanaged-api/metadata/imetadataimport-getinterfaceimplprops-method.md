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
ms.openlocfilehash: 1c9d9647084aa729817eeeb17ee3f5cd320c0d29
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491238"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="7ddcc-102">IMetaDataImport::GetInterfaceImplProps, méthode</span><span class="sxs-lookup"><span data-stu-id="7ddcc-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="7ddcc-103">Obtient un pointeur vers les jetons de métadonnées pour le <xref:System.Type> qui implémente la méthode spécifiée, et pour l’interface qui déclare cette méthode.</span><span class="sxs-lookup"><span data-stu-id="7ddcc-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="7ddcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ddcc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ddcc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ddcc-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="7ddcc-106">dans Jeton de métadonnées représentant la méthode pour laquelle retourner la classe et les jetons d’interface.</span><span class="sxs-lookup"><span data-stu-id="7ddcc-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="7ddcc-107">à Jeton de métadonnées représentant la classe qui implémente la méthode.</span><span class="sxs-lookup"><span data-stu-id="7ddcc-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="7ddcc-108">à Jeton de métadonnées représentant l’interface qui définit la méthode implémentée.</span><span class="sxs-lookup"><span data-stu-id="7ddcc-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="7ddcc-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="7ddcc-109">Remarks</span></span>

 <span data-ttu-id="7ddcc-110">Vous obtenez la valeur de `iImpl` en appelant la méthode [EnumInterfaceImpls,](imetadataimport-enuminterfaceimpls-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ddcc-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="7ddcc-111">Par exemple, supposez qu’une classe a une `mdTypeDef` valeur de jeton de 0x02000007 et qu’elle implémente trois interfaces dont les types ont des jetons :</span><span class="sxs-lookup"><span data-stu-id="7ddcc-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="7ddcc-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="7ddcc-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="7ddcc-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="7ddcc-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="7ddcc-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="7ddcc-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="7ddcc-115">Conceptuellement, ces informations sont stockées dans une table d’implémentation d’interface comme suit :</span><span class="sxs-lookup"><span data-stu-id="7ddcc-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="7ddcc-116">Numéro de ligne</span><span class="sxs-lookup"><span data-stu-id="7ddcc-116">Row number</span></span> | <span data-ttu-id="7ddcc-117">Jeton de classe</span><span class="sxs-lookup"><span data-stu-id="7ddcc-117">Class token</span></span> | <span data-ttu-id="7ddcc-118">Jeton d’interface</span><span class="sxs-lookup"><span data-stu-id="7ddcc-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="7ddcc-119">4</span><span class="sxs-lookup"><span data-stu-id="7ddcc-119">4</span></span>          |             |                 |
| <span data-ttu-id="7ddcc-120">5</span><span class="sxs-lookup"><span data-stu-id="7ddcc-120">5</span></span>          | <span data-ttu-id="7ddcc-121">02000007</span><span class="sxs-lookup"><span data-stu-id="7ddcc-121">02000007</span></span>    | <span data-ttu-id="7ddcc-122">02000003</span><span class="sxs-lookup"><span data-stu-id="7ddcc-122">02000003</span></span>        |
| <span data-ttu-id="7ddcc-123">6</span><span class="sxs-lookup"><span data-stu-id="7ddcc-123">6</span></span>          | <span data-ttu-id="7ddcc-124">02000007</span><span class="sxs-lookup"><span data-stu-id="7ddcc-124">02000007</span></span>    | <span data-ttu-id="7ddcc-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="7ddcc-125">0100000A</span></span>        |
| <span data-ttu-id="7ddcc-126">7</span><span class="sxs-lookup"><span data-stu-id="7ddcc-126">7</span></span>          |             |                 |
| <span data-ttu-id="7ddcc-127">8</span><span class="sxs-lookup"><span data-stu-id="7ddcc-127">8</span></span>          | <span data-ttu-id="7ddcc-128">02000007</span><span class="sxs-lookup"><span data-stu-id="7ddcc-128">02000007</span></span>    | <span data-ttu-id="7ddcc-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="7ddcc-129">0200001C</span></span>        |

<span data-ttu-id="7ddcc-130">Rappelez-vous que le jeton est une valeur de 4 octets :</span><span class="sxs-lookup"><span data-stu-id="7ddcc-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="7ddcc-131">Les 3 octets inférieurs contiennent le numéro de ligne, ou RID.</span><span class="sxs-lookup"><span data-stu-id="7ddcc-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="7ddcc-132">L’octet supérieur contient le type de jeton – 0x09 pour `mdtInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="7ddcc-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="7ddcc-133">`GetInterfaceImplProps`retourne les informations contenues dans la ligne dont vous indiquez le jeton dans l' `iImpl` argument.</span><span class="sxs-lookup"><span data-stu-id="7ddcc-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="7ddcc-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7ddcc-134">Requirements</span></span>  
 <span data-ttu-id="7ddcc-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ddcc-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ddcc-136">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7ddcc-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ddcc-137">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7ddcc-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ddcc-138">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ddcc-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddcc-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ddcc-139">See also</span></span>

- [<span data-ttu-id="7ddcc-140">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="7ddcc-140">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7ddcc-141">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="7ddcc-141">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
