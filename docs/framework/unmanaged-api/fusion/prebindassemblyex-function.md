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
ms.openlocfilehash: 8aa2d174200db76f5c7a6db43e14bb6904604226
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796327"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="a5162-102">Fonction PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="a5162-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="a5162-103">Obtient le nom complet de la stratégie d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="a5162-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="a5162-104">Cette fonction prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="a5162-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5162-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5162-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a5162-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5162-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="a5162-107">dans Identifie le contexte de l’application.</span><span class="sxs-lookup"><span data-stu-id="a5162-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="a5162-108">dans Identifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a5162-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="a5162-109">dans Identifie l’assembly parent.</span><span class="sxs-lookup"><span data-stu-id="a5162-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="a5162-110">Ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="a5162-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="a5162-111">dans Identifie la version du Runtime.</span><span class="sxs-lookup"><span data-stu-id="a5162-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="a5162-112">à Contient le nom complet de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="a5162-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a5162-113">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="a5162-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a5162-114">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="a5162-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5162-115">Notes</span><span class="sxs-lookup"><span data-stu-id="a5162-115">Remarks</span></span>  
 <span data-ttu-id="a5162-116">Le `ppNamePostPolicy` paramètre de sortie est défini uniquement si la fonction retourne HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="a5162-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="a5162-117">Dans le cas contraire, la valeur est null.</span><span class="sxs-lookup"><span data-stu-id="a5162-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5162-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a5162-118">Requirements</span></span>  
 <span data-ttu-id="a5162-119">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5162-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5162-120">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a5162-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a5162-121">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a5162-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5162-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5162-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5162-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5162-123">See also</span></span>

- [<span data-ttu-id="a5162-124">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="a5162-124">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
