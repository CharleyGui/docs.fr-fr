---
title: Comment afficher les arguments de ligne de C# commande-Guide de programmation
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 3ae2f65696c6661ab4f732b604267116996162b2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635169"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="a913b-102">Comment afficher les arguments de ligne deC# commande (Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="a913b-102">How to display command line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="a913b-103">Les arguments fournis à un fichier exécutable sur la ligne de commande sont accessibles à `Main` par l’intermédiaire d’un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="a913b-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="a913b-104">Les arguments sont fournis sous la forme d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a913b-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="a913b-105">Chaque élément du tableau contient un argument.</span><span class="sxs-lookup"><span data-stu-id="a913b-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="a913b-106">Les espaces blancs entre arguments sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="a913b-106">White-space between arguments is removed.</span></span> <span data-ttu-id="a913b-107">Par exemple, considérez ces appels de ligne de commande d’un fichier exécutable fictif :</span><span class="sxs-lookup"><span data-stu-id="a913b-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="a913b-108">Entrée sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a913b-108">Input on Command-line</span></span>|<span data-ttu-id="a913b-109">Tableau de chaînes passé à Main</span><span class="sxs-lookup"><span data-stu-id="a913b-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="a913b-110">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="a913b-110">**executable.exe a b c**</span></span>|<span data-ttu-id="a913b-111">"a"</span><span class="sxs-lookup"><span data-stu-id="a913b-111">"a"</span></span><br /><br /> <span data-ttu-id="a913b-112">"b"</span><span class="sxs-lookup"><span data-stu-id="a913b-112">"b"</span></span><br /><br /> <span data-ttu-id="a913b-113">"c"</span><span class="sxs-lookup"><span data-stu-id="a913b-113">"c"</span></span>|  
|<span data-ttu-id="a913b-114">**executable.exe un deux**</span><span class="sxs-lookup"><span data-stu-id="a913b-114">**executable.exe one two**</span></span>|<span data-ttu-id="a913b-115">"un"</span><span class="sxs-lookup"><span data-stu-id="a913b-115">"one"</span></span><br /><br /> <span data-ttu-id="a913b-116">"deux"</span><span class="sxs-lookup"><span data-stu-id="a913b-116">"two"</span></span>|  
|<span data-ttu-id="a913b-117">**executable.exe "un deux" trois**</span><span class="sxs-lookup"><span data-stu-id="a913b-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="a913b-118">"un deux"</span><span class="sxs-lookup"><span data-stu-id="a913b-118">"one two"</span></span><br /><br /> <span data-ttu-id="a913b-119">"trois"</span><span class="sxs-lookup"><span data-stu-id="a913b-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a913b-120">Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projets](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="a913b-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a913b-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="a913b-121">Example</span></span>  
 <span data-ttu-id="a913b-122">Cet exemple affiche les arguments de ligne de commande passés à une application de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a913b-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="a913b-123">La sortie présentée concerne la première entrée du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="a913b-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="a913b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a913b-124">See also</span></span>

- [<span data-ttu-id="a913b-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a913b-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a913b-126">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="a913b-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="a913b-127">Main() et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a913b-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="a913b-128">Valeurs de retour Main()</span><span class="sxs-lookup"><span data-stu-id="a913b-128">Main() Return Values</span></span>](./main-return-values.md)
