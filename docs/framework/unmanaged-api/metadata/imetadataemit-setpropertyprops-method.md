---
title: IMetaDataEmit::SetPropertyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007778"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="40ec2-102">IMetaDataEmit::SetPropertyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="40ec2-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="40ec2-103">Définit les fonctionnalités stockées dans les métadonnées d’une propriété définie par un appel antérieur à la [méthode DefineProperty](imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="40ec2-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ec2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40ec2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40ec2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="40ec2-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="40ec2-106">dans Jeton de la propriété à modifier.</span><span class="sxs-lookup"><span data-stu-id="40ec2-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="40ec2-107">dans Indicateurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="40ec2-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="40ec2-108">dans Type de la valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="40ec2-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="40ec2-109">dans Valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="40ec2-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="40ec2-110">dans Nombre de caractères (Unicode) dans `pValue` .</span><span class="sxs-lookup"><span data-stu-id="40ec2-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="40ec2-111">dans Méthode qui définit la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="40ec2-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="40ec2-112">dans Méthode qui obtient la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="40ec2-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="40ec2-113">dans Tableau d’autres méthodes associées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="40ec2-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="40ec2-114">Mettez fin à ce tableau avec un `mdTokenNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="40ec2-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40ec2-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="40ec2-115">Requirements</span></span>  
 <span data-ttu-id="40ec2-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ec2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ec2-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="40ec2-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40ec2-118">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40ec2-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40ec2-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40ec2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ec2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ec2-120">See also</span></span>

- [<span data-ttu-id="40ec2-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="40ec2-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="40ec2-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="40ec2-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
