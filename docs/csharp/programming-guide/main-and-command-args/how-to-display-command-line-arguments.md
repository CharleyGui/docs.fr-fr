---
title: 'Procédure : Afficher les arguments de ligne de commande - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: ba732930d08c74433d6ea7b38e7dc3a9fddf594c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923861"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="e99ae-102">Procédure : Afficher les arguments de ligne de commande (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e99ae-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="e99ae-103">Les arguments fournis à un fichier exécutable sur la ligne de commande sont accessibles à `Main` par l’intermédiaire d’un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="e99ae-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="e99ae-104">Les arguments sont fournis sous la forme d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="e99ae-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="e99ae-105">Chaque élément du tableau contient un argument.</span><span class="sxs-lookup"><span data-stu-id="e99ae-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="e99ae-106">Les espaces blancs entre arguments sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="e99ae-106">White-space between arguments is removed.</span></span> <span data-ttu-id="e99ae-107">Par exemple, considérez ces appels de ligne de commande d’un fichier exécutable fictif :</span><span class="sxs-lookup"><span data-stu-id="e99ae-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="e99ae-108">Entrée sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="e99ae-108">Input on Command-line</span></span>|<span data-ttu-id="e99ae-109">Tableau de chaînes passé à Main</span><span class="sxs-lookup"><span data-stu-id="e99ae-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="e99ae-110">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="e99ae-110">**executable.exe a b c**</span></span>|<span data-ttu-id="e99ae-111">"a"</span><span class="sxs-lookup"><span data-stu-id="e99ae-111">"a"</span></span><br /><br /> <span data-ttu-id="e99ae-112">"b"</span><span class="sxs-lookup"><span data-stu-id="e99ae-112">"b"</span></span><br /><br /> <span data-ttu-id="e99ae-113">"c"</span><span class="sxs-lookup"><span data-stu-id="e99ae-113">"c"</span></span>|  
|<span data-ttu-id="e99ae-114">**executable.exe un deux**</span><span class="sxs-lookup"><span data-stu-id="e99ae-114">**executable.exe one two**</span></span>|<span data-ttu-id="e99ae-115">"un"</span><span class="sxs-lookup"><span data-stu-id="e99ae-115">"one"</span></span><br /><br /> <span data-ttu-id="e99ae-116">"deux"</span><span class="sxs-lookup"><span data-stu-id="e99ae-116">"two"</span></span>|  
|<span data-ttu-id="e99ae-117">**executable.exe "un deux" trois**</span><span class="sxs-lookup"><span data-stu-id="e99ae-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="e99ae-118">"un deux"</span><span class="sxs-lookup"><span data-stu-id="e99ae-118">"one two"</span></span><br /><br /> <span data-ttu-id="e99ae-119">"trois"</span><span class="sxs-lookup"><span data-stu-id="e99ae-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e99ae-120">Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projets](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="e99ae-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e99ae-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="e99ae-121">Example</span></span>  
 <span data-ttu-id="e99ae-122">Cet exemple affiche les arguments de ligne de commande passés à une application de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e99ae-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="e99ae-123">La sortie présentée concerne la première entrée du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="e99ae-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e99ae-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e99ae-124">See also</span></span>

- [<span data-ttu-id="e99ae-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e99ae-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e99ae-126">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="e99ae-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="e99ae-127">Main() et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="e99ae-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="e99ae-128">Valeurs de retour Main()</span><span class="sxs-lookup"><span data-stu-id="e99ae-128">Main() Return Values</span></span>](./main-return-values.md)
