---
title: Assistant Débogage managé dllMainReturnsFalse
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 0b413521e0a2dc06c2ff0be642f080eaf541202f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216444"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="c1dd4-102">Assistant Débogage managé dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="c1dd4-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="c1dd4-103">L’Assistant Débogage managé `dllMainReturnsFalse` est activé si la fonction `DllMain` managée d’un assembly utilisateur, appelée avec la raison DLL_PROCESS_ATTACH, retourne FALSE.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c1dd4-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="c1dd4-104">Symptoms</span></span>  
 <span data-ttu-id="c1dd4-105">La fonction `DllMain` a retourné FALSE, indiquant qu’elle ne s’est pas exécuté correctement.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="c1dd4-106">Cela peut entraîner des problèmes indéterminés, car les fonctions `DllMain` contiennent généralement du code d’initialisation important.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c1dd4-107">Cause :</span><span class="sxs-lookup"><span data-stu-id="c1dd4-107">Cause</span></span>  
 <span data-ttu-id="c1dd4-108">La fonction `DllMain` est appelée avec la raison DLL_PROCESS_ATTACH pour l’initialisation de DLL lors du chargement.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="c1dd4-109">Si elle retourne FALSE, cela signifie que l’initialisation de la DLL a échoué.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c1dd4-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="c1dd4-110">Resolution</span></span>  
 <span data-ttu-id="c1dd4-111">Analysez le code de la fonction `DllMain` de la DLL ayant échoué, et identifiez la cause de l’échec d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c1dd4-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="c1dd4-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="c1dd4-113">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="c1dd4-114">Il fournit uniquement des données sur la valeur de retour pour `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c1dd4-115">Output</span><span class="sxs-lookup"><span data-stu-id="c1dd4-115">Output</span></span>  
 <span data-ttu-id="c1dd4-116">Un message indiquant qu’une fonction `DllMain`, appelée pour la raison DLL_PROCESS_ATTACH, a retourné FALSE.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="c1dd4-117">Notez que cet Assistant Débogage managé est activé uniquement si `DllMain` est implémenté dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="c1dd4-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c1dd4-118">Configuration</span><span class="sxs-lookup"><span data-stu-id="c1dd4-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1dd4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1dd4-119">See also</span></span>

- [<span data-ttu-id="c1dd4-120">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="c1dd4-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
