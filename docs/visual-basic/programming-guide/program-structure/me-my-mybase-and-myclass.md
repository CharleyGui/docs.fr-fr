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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347335"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="b72d9-102">Me, My, MyBase et MyClass dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b72d9-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="b72d9-103">`Me`, `My`, `MyBase`et `MyClass` dans Visual Basic ont des noms similaires, mais à des fins différentes.</span><span class="sxs-lookup"><span data-stu-id="b72d9-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="b72d9-104">Cette rubrique décrit chacune de ces entités afin de les distinguer.</span><span class="sxs-lookup"><span data-stu-id="b72d9-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="b72d9-105">Me</span><span class="sxs-lookup"><span data-stu-id="b72d9-105">Me</span></span>  
 <span data-ttu-id="b72d9-106">Le mot clé `Me` permet de faire référence à l’instance spécifique d’une classe ou d’une structure dans laquelle le code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b72d9-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="b72d9-107">`Me` se comporte comme une variable objet ou une variable de structure faisant référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="b72d9-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="b72d9-108">L’utilisation de `Me` est particulièrement utile pour transmettre des informations sur l’instance en cours d’exécution d’une classe ou d’une structure à une procédure d’une autre classe, structure ou module.</span><span class="sxs-lookup"><span data-stu-id="b72d9-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="b72d9-109">Par exemple, supposons que vous ayez la procédure suivante dans un module.</span><span class="sxs-lookup"><span data-stu-id="b72d9-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="b72d9-110">Vous pouvez appeler cette procédure et passer l’instance actuelle de la classe <xref:System.Windows.Forms.Form> en tant qu’argument à l’aide de l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="b72d9-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="b72d9-111">My</span><span class="sxs-lookup"><span data-stu-id="b72d9-111">My</span></span>  
 <span data-ttu-id="b72d9-112">La fonctionnalité `My` fournit un accès facile et intuitif à un certain nombre de .NET Framework classes, ce qui permet à l’utilisateur Visual Basic d’interagir avec l’ordinateur, l’application, les paramètres, les ressources, etc.</span><span class="sxs-lookup"><span data-stu-id="b72d9-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="b72d9-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="b72d9-113">MyBase</span></span>  
 <span data-ttu-id="b72d9-114">Le mot clé `MyBase` se comporte comme une variable objet qui fait référence à la classe de base de l’instance actuelle d’une classe.</span><span class="sxs-lookup"><span data-stu-id="b72d9-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="b72d9-115">`MyBase` est couramment utilisé pour accéder aux membres de la classe de base qui sont substitués ou occultés dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="b72d9-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="b72d9-116">`MyBase.New` est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="b72d9-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="b72d9-117">Classe</span><span class="sxs-lookup"><span data-stu-id="b72d9-117">MyClass</span></span>  
 <span data-ttu-id="b72d9-118">Le mot clé `MyClass` se comporte comme une variable objet qui fait référence à l’instance actuelle d’une classe telle qu’elle a été implémentée à l’origine.</span><span class="sxs-lookup"><span data-stu-id="b72d9-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="b72d9-119">`MyClass` est semblable à `Me`, mais tous les appels de méthode sur celui-ci sont traités comme si la méthode était `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="b72d9-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72d9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b72d9-120">See also</span></span>

- [<span data-ttu-id="b72d9-121">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="b72d9-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
