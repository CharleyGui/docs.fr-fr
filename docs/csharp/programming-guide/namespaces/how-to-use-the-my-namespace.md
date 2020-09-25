---
title: Comment utiliser l’espace de noms My-Guide de programmation C#
description: Apprenez-en davantage sur l’espace de noms My. L’espace de noms « My » offre un accès facile et intuitif à un certain nombre de classes .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 5310b911cc0abf0e82c4dc8efd45eb45ffb94c9d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176225"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="ef2b4-104">Comment utiliser l’espace de noms My (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ef2b4-104">How to use the My namespace (C# Programming Guide)</span></span>

<span data-ttu-id="ef2b4-105">L' <xref:Microsoft.VisualBasic.MyServices> espace de noms ( `My` dans Visual Basic) offre un accès facile et intuitif à plusieurs classes .net, ce qui vous permet d’écrire du code qui interagit avec l’ordinateur, l’application, les paramètres, les ressources, etc.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-105">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="ef2b4-106">Bien que conçu à l’origine pour une utilisation avec Visual Basic, l’espace de noms `MyServices` peut être utilisé dans les applications C#.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-106">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="ef2b4-107">Pour plus d’informations sur l’utilisation de l’espace de noms `MyServices` de Visual Basic, consultez [Développement avec My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef2b4-107">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="add-a-reference"></a><span data-ttu-id="ef2b4-108">Ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="ef2b4-108">Add a reference</span></span>

 <span data-ttu-id="ef2b4-109">Pour pouvoir utiliser les classes `MyServices` dans votre solution, vous devez d’abord ajouter une référence à la bibliothèque Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-109">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="ef2b4-110">Ajouter une référence à la bibliothèque de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef2b4-110">Add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="ef2b4-111">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références**, puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-111">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="ef2b4-112">Une fois la boîte de dialogue **Références** affichée, faites défiler la liste et sélectionnez Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-112">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="ef2b4-113">Vous pouvez aussi inclure la ligne suivante de la section `using` au début de votre programme.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-113">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="ef2b4-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="ef2b4-114">Example</span></span>  

 <span data-ttu-id="ef2b4-115">Cet exemple appelle plusieurs méthodes statiques contenues dans l’espace de noms `MyServices`.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-115">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="ef2b4-116">Pour compiler ce code, une référence à Microsoft.VisualBasic.DLL doit être ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-116">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="ef2b4-117">Certaines classes de l’espace de noms `MyServices` ne peuvent pas être appelées à partir d’une application C# : par exemple, la classe <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> n’est pas compatible.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-117">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="ef2b4-118">Dans ce cas particulier, les méthodes statiques, qui font partie intégrante de <xref:Microsoft.VisualBasic.FileIO.FileSystem> et qui sont aussi contenues dans VisualBasic.dll, peuvent être utilisées à la place.</span><span class="sxs-lookup"><span data-stu-id="ef2b4-118">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="ef2b4-119">Par exemple, voici comment utiliser une méthode de ce type pour dupliquer un répertoire :</span><span class="sxs-lookup"><span data-stu-id="ef2b4-119">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="ef2b4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef2b4-120">See also</span></span>

- [<span data-ttu-id="ef2b4-121">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ef2b4-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ef2b4-122">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="ef2b4-122">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="ef2b4-123">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="ef2b4-123">Using Namespaces</span></span>](./using-namespaces.md)
