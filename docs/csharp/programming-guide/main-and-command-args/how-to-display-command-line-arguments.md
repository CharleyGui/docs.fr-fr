---
title: Comment afficher les arguments de ligne de commande-Guide de programmation C#
description: Découvrez comment afficher les arguments de ligne de commande. Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 717e27c23724e63c03a38b028ef99dc6530b4745
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195478"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="b094f-104">Comment afficher des arguments de ligne de commande (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b094f-104">How to display command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="b094f-105">Les arguments fournis à un fichier exécutable sur la ligne de commande sont accessibles via un paramètre facultatif à `Main` .</span><span class="sxs-lookup"><span data-stu-id="b094f-105">Arguments provided to an executable on the command line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="b094f-106">Les arguments sont fournis sous la forme d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="b094f-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="b094f-107">Chaque élément du tableau contient un argument.</span><span class="sxs-lookup"><span data-stu-id="b094f-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="b094f-108">Les espaces blancs entre arguments sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="b094f-108">White-space between arguments is removed.</span></span> <span data-ttu-id="b094f-109">Par exemple, considérez ces appels de ligne de commande d’un fichier exécutable fictif :</span><span class="sxs-lookup"><span data-stu-id="b094f-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="b094f-110">Entrée sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b094f-110">Input on command line</span></span>|<span data-ttu-id="b094f-111">Tableau de chaînes passé à Main</span><span class="sxs-lookup"><span data-stu-id="b094f-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="b094f-112">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="b094f-112">**executable.exe a b c**</span></span>|<span data-ttu-id="b094f-113">"a"</span><span class="sxs-lookup"><span data-stu-id="b094f-113">"a"</span></span><br /><br /> <span data-ttu-id="b094f-114">"b"</span><span class="sxs-lookup"><span data-stu-id="b094f-114">"b"</span></span><br /><br /> <span data-ttu-id="b094f-115">"c"</span><span class="sxs-lookup"><span data-stu-id="b094f-115">"c"</span></span>|  
|<span data-ttu-id="b094f-116">**executable.exe un deux**</span><span class="sxs-lookup"><span data-stu-id="b094f-116">**executable.exe one two**</span></span>|<span data-ttu-id="b094f-117">"un"</span><span class="sxs-lookup"><span data-stu-id="b094f-117">"one"</span></span><br /><br /> <span data-ttu-id="b094f-118">"deux"</span><span class="sxs-lookup"><span data-stu-id="b094f-118">"two"</span></span>|  
|<span data-ttu-id="b094f-119">**executable.exe "un deux" trois**</span><span class="sxs-lookup"><span data-stu-id="b094f-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="b094f-120">"un deux"</span><span class="sxs-lookup"><span data-stu-id="b094f-120">"one two"</span></span><br /><br /> <span data-ttu-id="b094f-121">"trois"</span><span class="sxs-lookup"><span data-stu-id="b094f-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b094f-122">Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projets](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="b094f-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b094f-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="b094f-123">Example</span></span>  

 <span data-ttu-id="b094f-124">Cet exemple affiche les arguments de ligne de commande passés à une application de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b094f-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="b094f-125">La sortie présentée concerne la première entrée du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="b094f-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="b094f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b094f-126">See also</span></span>

- [<span data-ttu-id="b094f-127">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b094f-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b094f-128">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="b094f-128">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="b094f-129">Main () et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b094f-129">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="b094f-130">Valeurs de retour Main()</span><span class="sxs-lookup"><span data-stu-id="b094f-130">Main() Return Values</span></span>](./main-return-values.md)
