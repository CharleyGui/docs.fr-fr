---
title: Activation du débogage JIT-attach
description: Activez le débogage d’attachement juste-à-temps (JIT) pour attacher un débogueur à un processus lorsque vous rencontrez des erreurs. Elle peut être déclenchée par certaines méthodes ou fonctions.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416042"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="6f4a1-104">Activation du débogage JIT-attach</span><span class="sxs-lookup"><span data-stu-id="6f4a1-104">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="6f4a1-105">Débogage JIT-attach est l’expression utilisée pour décrire l’attachement d’un débogueur à un processus quand vous rencontrez des erreurs. Le débogage JIT-attach peut aussi être déclenché par des méthodes ou des fonctions spécifiques.</span><span class="sxs-lookup"><span data-stu-id="6f4a1-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="6f4a1-106">Le débogage JIT-attach est utilisé dans les conditions d’erreur suivantes :</span><span class="sxs-lookup"><span data-stu-id="6f4a1-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="6f4a1-107">Exceptions non gérées (dans le code natif et managé)</span><span class="sxs-lookup"><span data-stu-id="6f4a1-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="6f4a1-108">Méthode <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou fonction [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (famille Windows 7)</span><span class="sxs-lookup"><span data-stu-id="6f4a1-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="6f4a1-109">Erreurs irrécupérables du runtime</span><span class="sxs-lookup"><span data-stu-id="6f4a1-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="6f4a1-110">Le débogage JIT-attach est également déclenché par des appels aux fonctions et méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6f4a1-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="6f4a1-111">Méthode<xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6f4a1-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="6f4a1-112">Méthode<xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6f4a1-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="6f4a1-113">Fonction [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32)</span><span class="sxs-lookup"><span data-stu-id="6f4a1-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="6f4a1-114">Avant le .NET Framework 4, les .NET Framework fournissaient des clés de Registre distinctes pour contrôler le comportement des débogueurs natifs et gérés.</span><span class="sxs-lookup"><span data-stu-id="6f4a1-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="6f4a1-115">À partir de la .NET Framework 4, le contrôle est consolidé sous une clé de Registre unique : HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="6f4a1-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="6f4a1-116">Les valeurs que vous pouvez définir pour cette clé déterminent si un débogueur est appelé et, dans l’affirmative, s’il est appelé avec une boîte de dialogue qui nécessite une interaction utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6f4a1-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="6f4a1-117">Pour plus d’informations sur la définition de cette clé de Registre, consultez [configuration du débogage automatique](/windows/win32/debug/configuring-automatic-debugging).</span><span class="sxs-lookup"><span data-stu-id="6f4a1-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4a1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f4a1-118">See also</span></span>

- [<span data-ttu-id="6f4a1-119">Débogage, traçage et profilage</span><span class="sxs-lookup"><span data-stu-id="6f4a1-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="6f4a1-120">Simplification du débogage d’une image</span><span class="sxs-lookup"><span data-stu-id="6f4a1-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
