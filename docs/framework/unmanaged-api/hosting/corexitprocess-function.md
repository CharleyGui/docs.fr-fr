---
title: CorExitProcess, fonction
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: f6d8114732a3b7c15d0a0258a28a362d661b030a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673623"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="5c655-102">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="5c655-102">CorExitProcess Function</span></span>

<span data-ttu-id="5c655-103">Arrête le processus non managé actuel.</span><span class="sxs-lookup"><span data-stu-id="5c655-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="5c655-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5c655-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="5c655-105">Utilisez la méthode [ICLRMetaHost :: ExitProcess](iclrmetahost-exitprocess-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="5c655-105">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c655-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c655-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c655-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c655-107">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="5c655-108">Entier qui spécifie le code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="5c655-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c655-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="5c655-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c655-110">À partir du .NET Framework 4, `CorExitProcess` quitte chaque Runtime démarré dans le processus, pas seulement le runtime auquel les API héritées ont été liées.</span><span class="sxs-lookup"><span data-stu-id="5c655-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c655-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c655-111">Requirements</span></span>  

 <span data-ttu-id="5c655-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c655-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c655-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5c655-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c655-114">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c655-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c655-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c655-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c655-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c655-116">See also</span></span>

- [<span data-ttu-id="5c655-117">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="5c655-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
