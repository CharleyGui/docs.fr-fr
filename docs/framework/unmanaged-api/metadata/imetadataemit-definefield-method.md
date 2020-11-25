---
title: IMetaDataEmit::DefineField, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 2bc2b983171dc41d5ac37eda0359f1aaee4ebd6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725753"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="d6572-102">IMetaDataEmit::DefineField, méthode</span><span class="sxs-lookup"><span data-stu-id="d6572-102">IMetaDataEmit::DefineField Method</span></span>

<span data-ttu-id="d6572-103">Crée une définition pour un champ avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de champ.</span><span class="sxs-lookup"><span data-stu-id="d6572-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6572-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6572-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6572-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d6572-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="d6572-106">dans `mdTypeDef` Jeton de l’interface ou de la classe englobante.</span><span class="sxs-lookup"><span data-stu-id="d6572-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="d6572-107">dans Nom du champ en Unicode.</span><span class="sxs-lookup"><span data-stu-id="d6572-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="d6572-108">dans Attributs du champ.</span><span class="sxs-lookup"><span data-stu-id="d6572-108">[in] The field attributes.</span></span> <span data-ttu-id="d6572-109">Il s’agit d’un masque de `CorFieldAttr` valeur de valeurs.</span><span class="sxs-lookup"><span data-stu-id="d6572-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d6572-110">dans Signature de champ en tant qu’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="d6572-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d6572-111">dans Nombre d’octets dans `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="d6572-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d6572-112">dans `ELEMENT_TYPE_` *\** Pour la valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="d6572-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="d6572-113">Il s’agit d’une `CorElementType` valeur.</span><span class="sxs-lookup"><span data-stu-id="d6572-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="d6572-114">Si vous ne définissez pas de valeur de constante pour le champ, utilisez `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="d6572-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d6572-115">dans Valeur de constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="d6572-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d6572-116">dans Taille en (Unicode) caractères de `pValue` .</span><span class="sxs-lookup"><span data-stu-id="d6572-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="d6572-117">à `mdFieldDef` Jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="d6572-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6572-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d6572-118">Requirements</span></span>  

 <span data-ttu-id="d6572-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6572-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6572-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d6572-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6572-121">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6572-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6572-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6572-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6572-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6572-123">See also</span></span>

- [<span data-ttu-id="d6572-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d6572-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d6572-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d6572-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
