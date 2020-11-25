---
title: IMetaDataImport::EnumUserStrings, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: c7dcc740dcf9b228713693a57dc8ef96d215ebad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716562"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="c8f23-102">IMetaDataImport::EnumUserStrings, méthode</span><span class="sxs-lookup"><span data-stu-id="c8f23-102">IMetaDataImport::EnumUserStrings Method</span></span>

<span data-ttu-id="c8f23-103">Énumère les jetons String représentant des chaînes codées en dur dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="c8f23-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8f23-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8f23-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c8f23-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c8f23-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="c8f23-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c8f23-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c8f23-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="c8f23-108">à Tableau utilisé pour stocker les jetons de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c8f23-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c8f23-109">[in] Taille maximale du tableau `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="c8f23-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="c8f23-110">à Nombre de jetons de chaîne retournés dans `rStrings` .</span><span class="sxs-lookup"><span data-stu-id="c8f23-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8f23-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c8f23-111">Return Value</span></span>  
  
|<span data-ttu-id="c8f23-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8f23-112">HRESULT</span></span>|<span data-ttu-id="c8f23-113">Description</span><span class="sxs-lookup"><span data-stu-id="c8f23-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c8f23-114">`EnumUserStrings` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c8f23-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c8f23-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="c8f23-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c8f23-116">Dans ce cas, `pcStrings` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="c8f23-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8f23-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="c8f23-117">Remarks</span></span>  

 <span data-ttu-id="c8f23-118">Les jetons de chaîne sont créés par la méthode [IMetaDataEmit ::D efineuserstring](imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c8f23-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="c8f23-119">Cette méthode est conçue pour être utilisée par un navigateur de métadonnées plutôt que par un compilateur.</span><span class="sxs-lookup"><span data-stu-id="c8f23-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f23-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c8f23-120">Requirements</span></span>  

 <span data-ttu-id="c8f23-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8f23-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f23-122">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c8f23-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8f23-123">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8f23-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8f23-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8f23-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f23-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8f23-125">See also</span></span>

- [<span data-ttu-id="c8f23-126">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c8f23-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c8f23-127">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c8f23-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
