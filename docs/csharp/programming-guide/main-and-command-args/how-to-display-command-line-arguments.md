---
title: Comment afficher les arguments de ligne de commande-Guide de programmation C#
description: Découvrez comment afficher les arguments de ligne de commande. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 1ac5dc5a5f4e974c9202d2ce23f61071494e1977
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381812"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="3b945-104">Comment afficher des arguments de ligne de commande (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3b945-104">How to display command-line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="3b945-105">Les arguments fournis à un fichier exécutable sur la ligne de commande sont accessibles via un paramètre facultatif à `Main` .</span><span class="sxs-lookup"><span data-stu-id="3b945-105">Arguments provided to an executable on the command line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="3b945-106">Les arguments sont fournis sous la forme d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="3b945-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="3b945-107">Chaque élément du tableau contient un argument.</span><span class="sxs-lookup"><span data-stu-id="3b945-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="3b945-108">Les espaces blancs entre arguments sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="3b945-108">White-space between arguments is removed.</span></span> <span data-ttu-id="3b945-109">Par exemple, considérez ces appels de ligne de commande d’un fichier exécutable fictif :</span><span class="sxs-lookup"><span data-stu-id="3b945-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="3b945-110">Entrée sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="3b945-110">Input on command line</span></span>|<span data-ttu-id="3b945-111">Tableau de chaînes passé à Main</span><span class="sxs-lookup"><span data-stu-id="3b945-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="3b945-112">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="3b945-112">**executable.exe a b c**</span></span>|<span data-ttu-id="3b945-113">"a"</span><span class="sxs-lookup"><span data-stu-id="3b945-113">"a"</span></span><br /><br /> <span data-ttu-id="3b945-114">"b"</span><span class="sxs-lookup"><span data-stu-id="3b945-114">"b"</span></span><br /><br /> <span data-ttu-id="3b945-115">"c"</span><span class="sxs-lookup"><span data-stu-id="3b945-115">"c"</span></span>|  
|<span data-ttu-id="3b945-116">**executable.exe un deux**</span><span class="sxs-lookup"><span data-stu-id="3b945-116">**executable.exe one two**</span></span>|<span data-ttu-id="3b945-117">"un"</span><span class="sxs-lookup"><span data-stu-id="3b945-117">"one"</span></span><br /><br /> <span data-ttu-id="3b945-118">"deux"</span><span class="sxs-lookup"><span data-stu-id="3b945-118">"two"</span></span>|  
|<span data-ttu-id="3b945-119">**executable.exe "un deux" trois**</span><span class="sxs-lookup"><span data-stu-id="3b945-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="3b945-120">"un deux"</span><span class="sxs-lookup"><span data-stu-id="3b945-120">"one two"</span></span><br /><br /> <span data-ttu-id="3b945-121">"trois"</span><span class="sxs-lookup"><span data-stu-id="3b945-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3b945-122">Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projets](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="3b945-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b945-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b945-123">Example</span></span>  
 <span data-ttu-id="3b945-124">Cet exemple affiche les arguments de ligne de commande passés à une application de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3b945-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="3b945-125">La sortie présentée concerne la première entrée du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="3b945-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="3b945-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b945-126">See also</span></span>

- [<span data-ttu-id="3b945-127">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3b945-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b945-128">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="3b945-128">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="3b945-129">Main () et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="3b945-129">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="3b945-130">Valeurs de retour Main()</span><span class="sxs-lookup"><span data-stu-id="3b945-130">Main() Return Values</span></span>](./main-return-values.md)
