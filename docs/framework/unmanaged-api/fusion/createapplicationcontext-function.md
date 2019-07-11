---
title: CreateApplicationContext, fonction
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9853f974230ee755a33bc46ca6ba3e086051b236
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778468"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="cc883-102">CreateApplicationContext, fonction</span><span class="sxs-lookup"><span data-stu-id="cc883-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="cc883-103">Cette fonction prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.</span><span class="sxs-lookup"><span data-stu-id="cc883-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc883-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc883-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc883-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc883-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="cc883-106">[in] Pointeur vers un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="cc883-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="cc883-107">[out] Pointeur vers un contexte d’application.</span><span class="sxs-lookup"><span data-stu-id="cc883-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc883-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cc883-108">Requirements</span></span>  
 <span data-ttu-id="cc883-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc883-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc883-110">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="cc883-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cc883-111">**Bibliothèque :** Inclus en tant que ressource dans le fichier Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="cc883-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="cc883-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc883-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc883-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc883-113">See also</span></span>

- [<span data-ttu-id="cc883-114">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="cc883-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="cc883-115">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="cc883-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="cc883-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="cc883-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
