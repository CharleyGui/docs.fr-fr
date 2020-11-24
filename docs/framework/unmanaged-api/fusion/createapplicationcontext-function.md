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
ms.openlocfilehash: 9418be85f5b72bac8eed7f5ea4af4fc42439b01f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683227"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="64f81-102">CreateApplicationContext, fonction</span><span class="sxs-lookup"><span data-stu-id="64f81-102">CreateApplicationContext Function</span></span>

<span data-ttu-id="64f81-103">Cette fonction prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="64f81-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64f81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64f81-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="64f81-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="64f81-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="64f81-106">dans Pointeur vers un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="64f81-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="64f81-107">à Pointeur vers un contexte d’application.</span><span class="sxs-lookup"><span data-stu-id="64f81-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64f81-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="64f81-108">Requirements</span></span>  

 <span data-ttu-id="64f81-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64f81-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64f81-110">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="64f81-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="64f81-111">**Bibliothèque :** Inclus en tant que ressource dans Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="64f81-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="64f81-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64f81-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f81-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64f81-113">See also</span></span>

- [<span data-ttu-id="64f81-114">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="64f81-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="64f81-115">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="64f81-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="64f81-116">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="64f81-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
