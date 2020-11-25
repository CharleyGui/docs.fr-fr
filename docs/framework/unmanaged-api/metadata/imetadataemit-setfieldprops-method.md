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
ms.openlocfilehash: 0f98fb64b43822c437c39df2f3c51a222ef386b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730394"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="adb4d-102">IMetaDataEmit::SetFieldProps, méthode</span><span class="sxs-lookup"><span data-stu-id="adb4d-102">IMetaDataEmit::SetFieldProps Method</span></span>

<span data-ttu-id="adb4d-103">Définit ou met à jour la valeur par défaut pour le champ référencé par le jeton de champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="adb4d-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adb4d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adb4d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="adb4d-105">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="adb4d-106">dans Jeton pour le champ cible.</span><span class="sxs-lookup"><span data-stu-id="adb4d-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="adb4d-107">dans Attributs du champ.</span><span class="sxs-lookup"><span data-stu-id="adb4d-107">[in] Field attributes.</span></span> <span data-ttu-id="adb4d-108">Il s’agit d’un masque de `CorFieldAttr` valeur de valeurs.</span><span class="sxs-lookup"><span data-stu-id="adb4d-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="adb4d-109">dans `ELEMENT_TYPE_` *\** Pour la valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="adb4d-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="adb4d-110">Il s’agit d’une `CorElementType` valeur.</span><span class="sxs-lookup"><span data-stu-id="adb4d-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="adb4d-111">Si une constante n’est pas définie, définissez cette valeur sur `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="adb4d-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="adb4d-112">dans Valeur de constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="adb4d-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="adb4d-113">dans Taille, en caractères Unicode, de `pValue` .</span><span class="sxs-lookup"><span data-stu-id="adb4d-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adb4d-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="adb4d-114">Requirements</span></span>  

 <span data-ttu-id="adb4d-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adb4d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adb4d-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="adb4d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="adb4d-117">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="adb4d-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adb4d-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adb4d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb4d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adb4d-119">See also</span></span>

- [<span data-ttu-id="adb4d-120">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="adb4d-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="adb4d-121">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="adb4d-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
