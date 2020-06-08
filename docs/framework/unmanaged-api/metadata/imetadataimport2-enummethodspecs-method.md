---
title: IMetaDataImport2::EnumMethodSpecs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490716"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="97874-102">IMetaDataImport2::EnumMethodSpecs, méthode</span><span class="sxs-lookup"><span data-stu-id="97874-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="97874-103">Obtient un énumérateur pour un tableau de jetons MethodSpec associés au jeton MethodDef ou MemberRef spécifié.</span><span class="sxs-lookup"><span data-stu-id="97874-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97874-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97874-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="97874-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="97874-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="97874-106">[in, out] Pointeur vers l’énumérateur pour `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="97874-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="97874-107">dans Jeton MemberRef ou MethodDef qui représente la méthode dont les jetons MethodSpec doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="97874-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="97874-108">Si la valeur de `tk` est égale à 0 (zéro), tous les jetons MethodSpec dans l’étendue sont énumérés.</span><span class="sxs-lookup"><span data-stu-id="97874-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="97874-109">à Tableau de jetons MethodSpec à énumérer.</span><span class="sxs-lookup"><span data-stu-id="97874-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="97874-110">dans Nombre maximal de jetons demandés à placer dans `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="97874-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="97874-111">à Nombre retourné de jetons placés dans `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="97874-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97874-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="97874-112">Return Value</span></span>  
  
|<span data-ttu-id="97874-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97874-113">HRESULT</span></span>|<span data-ttu-id="97874-114">Description</span><span class="sxs-lookup"><span data-stu-id="97874-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="97874-115">`EnumMethodSpecs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="97874-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="97874-116">`phEnum`n’a aucun élément membre.</span><span class="sxs-lookup"><span data-stu-id="97874-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="97874-117">Dans ce cas, `pcMethodSpecs` a la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="97874-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97874-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="97874-118">Requirements</span></span>  
 <span data-ttu-id="97874-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97874-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97874-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="97874-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97874-121">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="97874-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97874-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97874-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97874-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97874-123">See also</span></span>

- [<span data-ttu-id="97874-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="97874-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="97874-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="97874-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
