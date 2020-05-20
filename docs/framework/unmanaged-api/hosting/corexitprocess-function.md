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
ms.openlocfilehash: a60805e1fd78cb14835957a7afc14fe279cb20fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616565"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="c7742-102">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="c7742-102">CorExitProcess Function</span></span>
<span data-ttu-id="c7742-103">Arrête le processus non managé actuel.</span><span class="sxs-lookup"><span data-stu-id="c7742-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="c7742-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c7742-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="c7742-105">Utilisez la méthode [ICLRMetaHost :: ExitProcess](iclrmetahost-exitprocess-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="c7742-105">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7742-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7742-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7742-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7742-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="c7742-108">Entier qui spécifie le code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="c7742-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7742-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c7742-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7742-110">À partir du .NET Framework 4, `CorExitProcess` quitte chaque Runtime démarré dans le processus, pas seulement le runtime auquel les API héritées ont été liées.</span><span class="sxs-lookup"><span data-stu-id="c7742-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7742-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="c7742-111">Requirements</span></span>  
 <span data-ttu-id="c7742-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7742-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7742-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c7742-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7742-114">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c7742-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7742-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7742-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7742-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7742-116">See also</span></span>

- [<span data-ttu-id="c7742-117">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="c7742-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
