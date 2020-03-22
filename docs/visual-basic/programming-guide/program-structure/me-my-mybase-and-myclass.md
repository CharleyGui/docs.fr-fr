---
title: Me, My, MyBase et MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400847"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="536ce-102">Me, My, MyBase et MyClass dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="536ce-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="536ce-103">`Me`, `My` `MyBase`, `MyClass` et dans Visual Basic ont des noms similaires, mais des buts différents.</span><span class="sxs-lookup"><span data-stu-id="536ce-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="536ce-104">Ce sujet décrit chacune de ces entités afin de les distinguer.</span><span class="sxs-lookup"><span data-stu-id="536ce-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="536ce-105">Moi</span><span class="sxs-lookup"><span data-stu-id="536ce-105">Me</span></span>  
 <span data-ttu-id="536ce-106">Le `Me` mot clé fournit un moyen de se référer à l’instance spécifique d’une classe ou d’une structure dans laquelle le code est actuellement en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="536ce-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="536ce-107">`Me`se comporte comme une variable d’objet ou une variable de structure se référant à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="536ce-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="536ce-108">L’utilisation `Me` est particulièrement utile pour transmettre des informations sur l’instance actuellement exécutante d’une classe ou d’une structure à une procédure dans une autre classe, structure ou module.</span><span class="sxs-lookup"><span data-stu-id="536ce-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="536ce-109">Supposons, par exemple, que vous ayez la procédure suivante dans un module.</span><span class="sxs-lookup"><span data-stu-id="536ce-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="536ce-110">Vous pouvez appeler cette procédure et passer <xref:System.Windows.Forms.Form> l’instance actuelle de la classe comme un argument en utilisant la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="536ce-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="536ce-111">My</span><span class="sxs-lookup"><span data-stu-id="536ce-111">My</span></span>  
 <span data-ttu-id="536ce-112">La `My` fonctionnalité offre un accès facile et intuitif à un certain nombre de classes cadre .NET, permettant à l’utilisateur visual basic d’interagir avec l’ordinateur, l’application, les paramètres, les ressources, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="536ce-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="536ce-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="536ce-113">MyBase</span></span>  
 <span data-ttu-id="536ce-114">Le `MyBase` mot clé se comporte comme une variable d’objet se référant à la classe de base de l’instance actuelle d’une classe.</span><span class="sxs-lookup"><span data-stu-id="536ce-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="536ce-115">`MyBase`est couramment utilisé pour accéder aux membres de la classe de base qui sont remplacés ou ombragés dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="536ce-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="536ce-116">`MyBase.New`est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivé.</span><span class="sxs-lookup"><span data-stu-id="536ce-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="536ce-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="536ce-117">MyClass</span></span>  
 <span data-ttu-id="536ce-118">Le `MyClass` mot clé se comporte comme une variable d’objet se référant à l’instance actuelle d’une classe telle qu’elle a été mise en œuvre à l’origine.</span><span class="sxs-lookup"><span data-stu-id="536ce-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="536ce-119">`MyClass`est similaire `Me`à , mais tous les appels méthode `NotOverridable`sur elle sont traitées comme si la méthode étaient .</span><span class="sxs-lookup"><span data-stu-id="536ce-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536ce-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="536ce-120">See also</span></span>

- [<span data-ttu-id="536ce-121">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="536ce-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
