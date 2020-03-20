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
ms.openlocfilehash: 44578595b3cb790570c5359e714bd39c109cf1f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176459"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="ac230-102">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="ac230-102">CorExitProcess Function</span></span>
<span data-ttu-id="ac230-103">Ferme le processus actuel non menté.</span><span class="sxs-lookup"><span data-stu-id="ac230-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="ac230-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="ac230-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="ac230-105">Utilisez la méthode [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="ac230-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac230-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac230-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac230-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac230-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="ac230-108">Un integer qui spécifie le code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="ac230-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac230-109">Notes </span><span class="sxs-lookup"><span data-stu-id="ac230-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac230-110">En commençant par le cadre `CorExitProcess` .NET 4, quitte chaque runtime commencé dans le processus, pas seulement le temps d’exécution auquel les API hérités ont été liés.</span><span class="sxs-lookup"><span data-stu-id="ac230-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac230-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ac230-111">Requirements</span></span>  
 <span data-ttu-id="ac230-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac230-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac230-113">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="ac230-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac230-114">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="ac230-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac230-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac230-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac230-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac230-116">See also</span></span>

- [<span data-ttu-id="ac230-117">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="ac230-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
