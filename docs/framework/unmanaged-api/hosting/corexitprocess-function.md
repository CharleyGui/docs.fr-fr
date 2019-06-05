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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a28b33f80299ae6fce34f9de66b6f7f1bc70ef6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490570"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="bfcfb-102">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="bfcfb-102">CorExitProcess Function</span></span>
<span data-ttu-id="bfcfb-103">Arrête le processus non managé en cours.</span><span class="sxs-lookup"><span data-stu-id="bfcfb-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="bfcfb-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bfcfb-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="bfcfb-105">Utilisez le [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="bfcfb-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfcfb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfcfb-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfcfb-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bfcfb-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="bfcfb-108">Entier qui spécifie le code de sortie.</span><span class="sxs-lookup"><span data-stu-id="bfcfb-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfcfb-109">Notes</span><span class="sxs-lookup"><span data-stu-id="bfcfb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfcfb-110">Commençant par le .NET Framework 4, `CorExitProcess` quitte chaque exécution commencée dans le processus, pas uniquement le runtime auquel les API héritées ont été liés.</span><span class="sxs-lookup"><span data-stu-id="bfcfb-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfcfb-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bfcfb-111">Requirements</span></span>  
 <span data-ttu-id="bfcfb-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfcfb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfcfb-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bfcfb-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfcfb-114">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bfcfb-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfcfb-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfcfb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfcfb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfcfb-116">See also</span></span>

- [<span data-ttu-id="bfcfb-117">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="bfcfb-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
