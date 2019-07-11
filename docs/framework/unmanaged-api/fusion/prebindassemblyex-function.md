---
title: Fonction PreBindAssemblyEx
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a23d3c4fd8eef2e361abf1602157cb4fbb820b48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773863"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="9ed52-102">Fonction PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="9ed52-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="9ed52-103">Obtient le nom complet de la stratégie après d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="9ed52-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="9ed52-104">Cette fonction prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.</span><span class="sxs-lookup"><span data-stu-id="9ed52-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed52-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ed52-105">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ed52-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ed52-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="9ed52-107">[in] Identifie le contexte de l’application.</span><span class="sxs-lookup"><span data-stu-id="9ed52-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="9ed52-108">[in] Identifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9ed52-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="9ed52-109">[in] Identifie l’assembly parent.</span><span class="sxs-lookup"><span data-stu-id="9ed52-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="9ed52-110">Ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="9ed52-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="9ed52-111">[in] Identifie la version du runtime.</span><span class="sxs-lookup"><span data-stu-id="9ed52-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="9ed52-112">[out] Contient le nom complet de la stratégie après.</span><span class="sxs-lookup"><span data-stu-id="9ed52-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="9ed52-113">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="9ed52-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9ed52-114">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="9ed52-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ed52-115">Notes</span><span class="sxs-lookup"><span data-stu-id="9ed52-115">Remarks</span></span>  
 <span data-ttu-id="9ed52-116">Le `ppNamePostPolicy` paramètre de sortie est défini uniquement si la fonction retourne HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="9ed52-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="9ed52-117">Sinon, elle a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="9ed52-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed52-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ed52-118">Requirements</span></span>  
 <span data-ttu-id="9ed52-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed52-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed52-120">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9ed52-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9ed52-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ed52-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ed52-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed52-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed52-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ed52-123">See also</span></span>

- [<span data-ttu-id="9ed52-124">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="9ed52-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
