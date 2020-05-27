---
title: IMetaDataEmit::DefineProperty, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: 479cb25ad8e1c263d3539a4203ac5bea781eb931
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009374"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="d3f5d-102">IMetaDataEmit::DefineProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="d3f5d-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="d3f5d-103">Crée une définition de propriété pour le type spécifié, avec les `get` accesseurs de méthode et spécifiés `set` , et obtient un jeton pour cette définition de propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3f5d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3f5d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3f5d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d3f5d-106">dans Jeton de la classe ou de l’interface sur laquelle la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="d3f5d-107">[in] Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="d3f5d-108">dans Indicateurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="d3f5d-109">dans Signature de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d3f5d-110">dans Nombre d’octets dans `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="d3f5d-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d3f5d-111">dans Type de la valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d3f5d-112">dans Valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d3f5d-113">dans Nombre de caractères (Unicode) dans `pValue` .</span><span class="sxs-lookup"><span data-stu-id="d3f5d-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="d3f5d-114">dans Méthode qui définit la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="d3f5d-115">dans Méthode qui obtient la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="d3f5d-116">dans Tableau d’autres méthodes associées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="d3f5d-117">Terminez le tableau par un `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="d3f5d-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="d3f5d-118">à `mdProperty`Jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="d3f5d-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3f5d-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d3f5d-119">Requirements</span></span>  
 <span data-ttu-id="d3f5d-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3f5d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3f5d-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d3f5d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3f5d-122">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3f5d-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3f5d-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f5d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f5d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3f5d-124">See also</span></span>

- [<span data-ttu-id="d3f5d-125">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d3f5d-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d3f5d-126">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d3f5d-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
