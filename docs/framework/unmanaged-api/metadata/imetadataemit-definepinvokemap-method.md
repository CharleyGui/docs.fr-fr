---
title: IMetaDataEmit::DefinePinvokeMap, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: 447ec44ed3efc4eec84d1e4acd6f2ec1a730bf74
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008025"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="d3909-102">IMetaDataEmit::DefinePinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="d3909-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="d3909-103">Définit les fonctionnalités de la signature PInvoke de la méthode référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="d3909-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3909-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3909-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3909-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3909-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d3909-106">dans Jeton pour la méthode cible.</span><span class="sxs-lookup"><span data-stu-id="d3909-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="d3909-107">dans Indicateurs utilisés par PInvoke pour effectuer le mappage.</span><span class="sxs-lookup"><span data-stu-id="d3909-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="d3909-108">dans Nom de la méthode d’exportation cible dans une DLL non managée.</span><span class="sxs-lookup"><span data-stu-id="d3909-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="d3909-109">dans Jeton pour la DLL native cible.</span><span class="sxs-lookup"><span data-stu-id="d3909-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3909-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d3909-110">Requirements</span></span>  
 <span data-ttu-id="d3909-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3909-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3909-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d3909-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3909-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3909-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3909-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3909-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3909-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3909-115">See also</span></span>

- [<span data-ttu-id="d3909-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d3909-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d3909-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d3909-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
