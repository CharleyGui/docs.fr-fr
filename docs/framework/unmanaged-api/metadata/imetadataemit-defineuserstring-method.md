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
ms.openlocfilehash: ed3c20fe8272ca3205079d26df0b7bde12e58307
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732695"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="3ef2e-102">IMetaDataEmit::DefineUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="3ef2e-102">IMetaDataEmit::DefineUserString Method</span></span>

<span data-ttu-id="3ef2e-103">Obtient un jeton de métadonnées pour la chaîne littérale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3ef2e-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ef2e-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ef2e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3ef2e-105">Parameters</span></span>  

 `szString`  
 <span data-ttu-id="3ef2e-106">dans Chaîne utilisateur à stocker.</span><span class="sxs-lookup"><span data-stu-id="3ef2e-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="3ef2e-107">dans Nombre de caractères larges dans `szString` .</span><span class="sxs-lookup"><span data-stu-id="3ef2e-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="3ef2e-108">à Jeton de chaîne assigné.</span><span class="sxs-lookup"><span data-stu-id="3ef2e-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ef2e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3ef2e-109">Requirements</span></span>  

 <span data-ttu-id="3ef2e-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ef2e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ef2e-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3ef2e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ef2e-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ef2e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ef2e-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ef2e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef2e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ef2e-114">See also</span></span>

- [<span data-ttu-id="3ef2e-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="3ef2e-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3ef2e-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="3ef2e-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
