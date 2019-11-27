---
title: IMetaDataEmit::SetParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 813460aa027b259866b168d426fd28502b5c4465
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432496"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="94a94-102">IMetaDataEmit::SetParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="94a94-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="94a94-103">Définit ou modifie les fonctionnalités d’un paramètre de méthode qui a été défini par un appel antérieur à [IMetaDataEmit ::D efineparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="94a94-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94a94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94a94-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94a94-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="94a94-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="94a94-106">dans Jeton pour le paramètre cible.</span><span class="sxs-lookup"><span data-stu-id="94a94-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="94a94-107">dans Nom du paramètre en Unicode.</span><span class="sxs-lookup"><span data-stu-id="94a94-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="94a94-108">dans Indicateurs du paramètre.</span><span class="sxs-lookup"><span data-stu-id="94a94-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="94a94-109">dans ELEMENT_TYPE_ \* pour la valeur constante.</span><span class="sxs-lookup"><span data-stu-id="94a94-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="94a94-110">dans Valeur de constante pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="94a94-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="94a94-111">dans Taille en caractères (Unicode) de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="94a94-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94a94-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="94a94-112">Requirements</span></span>  
 <span data-ttu-id="94a94-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94a94-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94a94-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="94a94-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94a94-115">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="94a94-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94a94-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94a94-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a94-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94a94-117">See also</span></span>

- [<span data-ttu-id="94a94-118">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="94a94-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="94a94-119">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="94a94-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
