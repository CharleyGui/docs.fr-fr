---
title: 'Procédure : gérer des exceptions dans des boucles parallèles'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 87405425e85ed16d10b3e8b382c6e414fff10ddf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278530"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="bfab1-102">Procédure : gérer des exceptions dans des boucles parallèles</span><span class="sxs-lookup"><span data-stu-id="bfab1-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="bfab1-103">Les surcharges <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ne possèdent pas de mécanisme permettant de gérer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="bfab1-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="bfab1-104">À cet égard, elles ressemblent à des `for` boucles normales et `foreach` ( `For` et `For Each` dans Visual Basic); une exception non gérée entraîne l’arrêt de la boucle dès que toutes les itérations en cours se terminent.</span><span class="sxs-lookup"><span data-stu-id="bfab1-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="bfab1-105">Quand vous ajoutez votre propre logique de gestion des exceptions à des boucles parallèles, gérez le cas dans lequel de telles exceptions peuvent être levées simultanément sur plusieurs threads et le cas dans lequel une exception levée sur un thread provoque la levée d'une autre exception sur un autre thread.</span><span class="sxs-lookup"><span data-stu-id="bfab1-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="bfab1-106">Vous pouvez gérer les deux cas en encapsulant toutes les exceptions de la boucle dans un <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfab1-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bfab1-107">L'exemple suivant montre une méthode possible.</span><span class="sxs-lookup"><span data-stu-id="bfab1-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfab1-108">Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bfab1-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="bfab1-109">Cette erreur est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="bfab1-109">This error is benign.</span></span> <span data-ttu-id="bfab1-110">Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans l'exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="bfab1-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="bfab1-111">Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.</span><span class="sxs-lookup"><span data-stu-id="bfab1-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfab1-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="bfab1-112">Example</span></span>  
 <span data-ttu-id="bfab1-113">Dans cet exemple, toutes les exceptions sont interceptées, puis encapsulées dans une <xref:System.AggregateException?displayProperty=nameWithType> qui est ensuite levée.</span><span class="sxs-lookup"><span data-stu-id="bfab1-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="bfab1-114">L'appelant peut décider des exceptions à gérer.</span><span class="sxs-lookup"><span data-stu-id="bfab1-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="bfab1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfab1-115">See also</span></span>

- [<span data-ttu-id="bfab1-116">Parallélisme des données</span><span class="sxs-lookup"><span data-stu-id="bfab1-116">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="bfab1-117">Expressions lambda dans PLINQ et TPL</span><span class="sxs-lookup"><span data-stu-id="bfab1-117">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
