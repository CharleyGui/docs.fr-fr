---
title: IMetaDataImport2::EnumGenericParams, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 6b1a8e66eea6caec9dfc8d99e343c987cefa1b0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702756"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="cba01-102">IMetaDataImport2::EnumGenericParams, méthode</span><span class="sxs-lookup"><span data-stu-id="cba01-102">IMetaDataImport2::EnumGenericParams Method</span></span>

<span data-ttu-id="cba01-103">Obtient un énumérateur pour un tableau de jetons de paramètres génériques associés au jeton TypeDef ou MethodDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="cba01-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cba01-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cba01-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cba01-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="cba01-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="cba01-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="cba01-107">dans Jeton TypeDef ou MethodDef dont les paramètres génériques doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="cba01-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="cba01-108">à Tableau de paramètres génériques à énumérer.</span><span class="sxs-lookup"><span data-stu-id="cba01-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cba01-109">dans Nombre maximal de jetons demandés à placer dans `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="cba01-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="cba01-110">à Nombre retourné de jetons placés dans `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="cba01-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cba01-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="cba01-111">Return Value</span></span>  
  
|<span data-ttu-id="cba01-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cba01-112">HRESULT</span></span>|<span data-ttu-id="cba01-113">Description</span><span class="sxs-lookup"><span data-stu-id="cba01-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cba01-114">`EnumGenericParams` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cba01-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cba01-115">`phEnum` n’a aucun élément membre.</span><span class="sxs-lookup"><span data-stu-id="cba01-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="cba01-116">Dans ce cas, `pcGenericParams` a la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="cba01-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cba01-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cba01-117">Requirements</span></span>  

 <span data-ttu-id="cba01-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cba01-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cba01-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cba01-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cba01-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cba01-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cba01-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cba01-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba01-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cba01-122">See also</span></span>

- [<span data-ttu-id="cba01-123">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="cba01-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="cba01-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="cba01-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
