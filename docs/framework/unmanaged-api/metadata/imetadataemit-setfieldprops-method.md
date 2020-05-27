---
title: IMetaDataEmit::SetFieldProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: 220556ec130c7bff7c413405820c4fee0582b051
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008012"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="43207-102">IMetaDataEmit::SetFieldProps, méthode</span><span class="sxs-lookup"><span data-stu-id="43207-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="43207-103">Définit ou met à jour la valeur par défaut pour le champ référencé par le jeton de champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="43207-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43207-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43207-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43207-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="43207-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="43207-106">dans Jeton pour le champ cible.</span><span class="sxs-lookup"><span data-stu-id="43207-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="43207-107">dans Attributs du champ.</span><span class="sxs-lookup"><span data-stu-id="43207-107">[in] Field attributes.</span></span> <span data-ttu-id="43207-108">Il s’agit d’un masque de `CorFieldAttr` valeur de valeurs.</span><span class="sxs-lookup"><span data-stu-id="43207-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="43207-109">dans `ELEMENT_TYPE_` *\** Pour la valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="43207-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="43207-110">Il s’agit d’une `CorElementType` valeur.</span><span class="sxs-lookup"><span data-stu-id="43207-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="43207-111">Si une constante n’est pas définie, définissez cette valeur sur `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="43207-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="43207-112">dans Valeur de constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="43207-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="43207-113">dans Taille, en caractères Unicode, de `pValue` .</span><span class="sxs-lookup"><span data-stu-id="43207-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43207-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="43207-114">Requirements</span></span>  
 <span data-ttu-id="43207-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43207-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43207-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="43207-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43207-117">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="43207-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43207-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43207-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43207-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43207-119">See also</span></span>

- [<span data-ttu-id="43207-120">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="43207-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="43207-121">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="43207-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
