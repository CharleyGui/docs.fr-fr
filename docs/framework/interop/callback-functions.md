---
title: Fonctions de rappel
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 0fbf6df93e3ef9ee6380ed35f98018d157599e2a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123743"
---
# <a name="callback-functions"></a><span data-ttu-id="74042-102">Fonctions de rappel</span><span class="sxs-lookup"><span data-stu-id="74042-102">Callback Functions</span></span>
<span data-ttu-id="74042-103">Une fonction de rappel désigne du code figurant dans une application managée qui permet à une fonction DLL non managée d’effectuer une tâche.</span><span class="sxs-lookup"><span data-stu-id="74042-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="74042-104">Les appels à une fonction de rappel sont indirectement passés depuis une application managée via une fonction DLL avant de revenir à l’implémentation managée.</span><span class="sxs-lookup"><span data-stu-id="74042-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="74042-105">Certaines des nombreuses fonctions DLL appelées à l’aide de l’appel de code non managé nécessitent une fonction de rappel dans du code managé pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="74042-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="74042-106">Pour appeler la plupart des fonctions DLL à partir d’un code managé, il vous suffit de créer une définition managée de la fonction, puis de l’appeler.</span><span class="sxs-lookup"><span data-stu-id="74042-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="74042-107">La procédure est simple.</span><span class="sxs-lookup"><span data-stu-id="74042-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="74042-108">L’utilisation d’une fonction DLL nécessitant une fonction de rappel implique des étapes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="74042-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="74042-109">Vous devez d’abord déterminer si la fonction nécessite un rappel en consultant la documentation sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="74042-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="74042-110">Vous devez ensuite créer la fonction de rappel dans votre application managée.</span><span class="sxs-lookup"><span data-stu-id="74042-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="74042-111">Vous devez enfin appeler la fonction DLL, en passant un pointeur vers la fonction de rappel sous la forme d’un argument.</span><span class="sxs-lookup"><span data-stu-id="74042-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span> 
 
 <span data-ttu-id="74042-112">L’illustration suivante résume la fonction de rappel et les étapes de l’implémentation :</span><span class="sxs-lookup"><span data-stu-id="74042-112">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagramme illustrant le processus de rappel de l’appel de code non managé.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="74042-114">Les fonctions de rappel sont idéales dans les cas où une tâche est effectuée à maintes reprises.</span><span class="sxs-lookup"><span data-stu-id="74042-114">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="74042-115">Elles sont aussi fréquemment utilisées avec des fonctions d’énumération, comme **EnumFontFamilies**, **EnumPrinters** et **EnumWindows**, dans l’interface API Windows.</span><span class="sxs-lookup"><span data-stu-id="74042-115">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="74042-116">La fonction **EnumWindows** se décline dans toutes les fenêtres existantes de votre ordinateur ; dans chacune, elle appelle la fonction de rappel pour exécuter une tâche.</span><span class="sxs-lookup"><span data-stu-id="74042-116">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="74042-117">Pour obtenir des instructions et un exemple, consultez [Guide pratique pour implémenter des fonctions de rappel](how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="74042-117">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74042-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74042-118">See also</span></span>

- [<span data-ttu-id="74042-119">Comment : implémenter des fonctions de rappel</span><span class="sxs-lookup"><span data-stu-id="74042-119">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="74042-120">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="74042-120">Calling a DLL Function</span></span>](calling-a-dll-function.md)
