---
title: IMetaDataEmit::SetPinvokeMap, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 236fc848087f64c2327c2c9e790065cc3f64dc58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704303"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="14a24-102">IMetaDataEmit::SetPinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="14a24-102">IMetaDataEmit::SetPinvokeMap Method</span></span>

<span data-ttu-id="14a24-103">Définit ou modifie les fonctionnalités de la signature PInvoke d’une méthode, comme défini par un appel antérieur à [IMetaDataEmit ::D efinepinvokemap](imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="14a24-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14a24-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14a24-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="14a24-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="14a24-106">dans Auquel les `mdToken` informations de mappage s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="14a24-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="14a24-107">dans Indicateurs utilisés par PInvoke pour effectuer le mappage.</span><span class="sxs-lookup"><span data-stu-id="14a24-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="14a24-108">Il s’agit d’un masque de `CorPinvokeMap` valeur de valeurs.</span><span class="sxs-lookup"><span data-stu-id="14a24-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="14a24-109">dans Nom de l’exportation cible dans la DLL native.</span><span class="sxs-lookup"><span data-stu-id="14a24-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="14a24-110">dans `mdModuleRef` Jeton pour la dll non managée cible.</span><span class="sxs-lookup"><span data-stu-id="14a24-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14a24-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="14a24-111">Requirements</span></span>  

 <span data-ttu-id="14a24-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a24-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a24-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="14a24-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14a24-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14a24-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14a24-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a24-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a24-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14a24-116">See also</span></span>

- [<span data-ttu-id="14a24-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="14a24-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="14a24-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="14a24-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
