---
title: IMetaDataEmit2::SetGenericParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 8feba8e67f3a90dd48fd957065a9c166c204b87c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492731"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="114b7-102">IMetaDataEmit2::SetGenericParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="114b7-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="114b7-103">Définit des valeurs de propriété pour la définition de paramètre générique référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="114b7-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="114b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="114b7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="114b7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="114b7-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="114b7-106">dans Jeton pour la définition de paramètre générique pour laquelle définir des valeurs.</span><span class="sxs-lookup"><span data-stu-id="114b7-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="114b7-107">dans Valeur de l’énumération [CorGenericParamAttr,](corgenericparamattr-enumeration.md) qui décrit le type du paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="114b7-107">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="114b7-108">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="114b7-108">[in] Optional.</span></span> <span data-ttu-id="114b7-109">Nom du paramètre pour lequel des valeurs doivent être définies.</span><span class="sxs-lookup"><span data-stu-id="114b7-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="114b7-110">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="114b7-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="114b7-111">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="114b7-111">[in] Optional.</span></span> <span data-ttu-id="114b7-112">Tableau de contraintes de type se terminant par zéro.</span><span class="sxs-lookup"><span data-stu-id="114b7-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="114b7-113">Les membres de tableau doivent être un `mdTypeDef` `mdTypeRef` jeton de `mdTypeSpec` métadonnées, ou.</span><span class="sxs-lookup"><span data-stu-id="114b7-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="114b7-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="114b7-114">Requirements</span></span>  
 <span data-ttu-id="114b7-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="114b7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="114b7-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="114b7-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="114b7-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="114b7-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="114b7-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="114b7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114b7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="114b7-119">See also</span></span>

- [<span data-ttu-id="114b7-120">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="114b7-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="114b7-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="114b7-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
