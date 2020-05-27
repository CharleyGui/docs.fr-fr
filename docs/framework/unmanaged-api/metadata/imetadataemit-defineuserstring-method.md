---
title: IMetaDataEmit::DefineUserString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: def77bb64e21b1421983cf263d488ecc1ddb9452
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009317"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="845bd-102">IMetaDataEmit::DefineUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="845bd-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="845bd-103">Obtient un jeton de métadonnées pour la chaîne littérale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="845bd-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="845bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="845bd-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="845bd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="845bd-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="845bd-106">dans Chaîne utilisateur à stocker.</span><span class="sxs-lookup"><span data-stu-id="845bd-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="845bd-107">dans Nombre de caractères larges dans `szString` .</span><span class="sxs-lookup"><span data-stu-id="845bd-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="845bd-108">à Jeton de chaîne assigné.</span><span class="sxs-lookup"><span data-stu-id="845bd-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="845bd-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="845bd-109">Requirements</span></span>  
 <span data-ttu-id="845bd-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="845bd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="845bd-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="845bd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="845bd-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="845bd-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="845bd-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="845bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845bd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="845bd-114">See also</span></span>

- [<span data-ttu-id="845bd-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="845bd-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="845bd-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="845bd-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
