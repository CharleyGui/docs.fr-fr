---
title: Accès d'un membre partagé via une instance ; l'expression qualifiante ne sera pas évaluée
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 311f4c025072162e0cfb6b87587f8602d33fcd19
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646866"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a><span data-ttu-id="b7147-102">Accès d'un membre partagé via une instance ; l'expression qualifiante ne sera pas évaluée</span><span class="sxs-lookup"><span data-stu-id="b7147-102">Access of shared member through an instance; qualifying expression will not be evaluated</span></span>
<span data-ttu-id="b7147-103">Une variable d’instance d’une classe ou une structure est utilisée pour accéder à un `Shared` variable, la propriété, la procédure ou événement défini dans cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b7147-103">An instance variable of a class or structure is used to access a `Shared` variable, property, procedure, or event defined in that class or structure.</span></span> <span data-ttu-id="b7147-104">Cet avertissement peut également se produire si une variable d’instance est utilisée pour accéder à un membre implicitement partagé d’une classe ou une structure, comme une constante ou énumération, ou une classe imbriquée ou une structure.</span><span class="sxs-lookup"><span data-stu-id="b7147-104">This warning can also occur if an instance variable is used to access an implicitly shared member of a class or structure, such as a constant or enumeration, or a nested class or structure.</span></span>  
  
 <span data-ttu-id="b7147-105">Le partage d’un membre vise à créer une seule copie de ce membre et le rendre disponible à chaque instance de la classe ou structure dans laquelle elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="b7147-105">The purpose of sharing a member is to create only a single copy of that member and make that single copy available to every instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="b7147-106">Il est cohérent avec cet effet pour accéder à un `Shared` membre via le nom de sa classe ou structure, plutôt que via une variable qui conserve une instance de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="b7147-106">It is consistent with this purpose to access a `Shared` member through the name of its class or structure, rather than through a variable that holds an individual instance of that class or structure.</span></span>  
  
 <span data-ttu-id="b7147-107">L’accès à un `Shared` membre via une variable d’instance peut rendre votre code plus difficile à comprendre en occultant le fait que le membre est `Shared`.</span><span class="sxs-lookup"><span data-stu-id="b7147-107">Accessing a `Shared` member through an instance variable can make your code more difficult to understand by obscuring the fact that the member is `Shared`.</span></span> <span data-ttu-id="b7147-108">En outre, si ce type d’accès fait partie d’une expression qui exécute d’autres actions, comme un `Function` procédure qui retourne une instance du membre partagé, Visual Basic ignore l’expression et toutes les autres actions il exécuterait dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="b7147-108">Furthermore, if such access is part of an expression that performs other actions, such as a `Function` procedure that returns an instance of the shared member, Visual Basic bypasses the expression and any other actions it would otherwise perform.</span></span>  
  
 <span data-ttu-id="b7147-109">Pour plus d’informations et un exemple, consultez [partagé](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="b7147-109">For more information and an example, see [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
 <span data-ttu-id="b7147-110">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="b7147-110">By default, this message is a warning.</span></span> <span data-ttu-id="b7147-111">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b7147-111">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b7147-112">**ID d’erreur :** BC42025</span><span class="sxs-lookup"><span data-stu-id="b7147-112">**Error ID:** BC42025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b7147-113">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b7147-113">To correct this error</span></span>  
  
- <span data-ttu-id="b7147-114">Utilisez le nom de la classe ou structure qui définit le `Shared` membre à y accéder, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b7147-114">Use the name of the class or structure that defines the `Shared` member to access it, as shown in the following example.</span></span>  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="b7147-115">Être alerte pour les effets de la portée lorsque deux éléments de programmation portent le même nom.</span><span class="sxs-lookup"><span data-stu-id="b7147-115">Be alert for the effects of scope when two programming elements have the same name.</span></span> <span data-ttu-id="b7147-116">Dans l’exemple précédent, si vous déclarez une instance à l’aide de `Dim testClass as testClass = Nothing`, le compilateur traite un appel à `testClass.sayHello()` comme un accès de la méthode via le nom de classe et aucun avertissement se produit.</span><span class="sxs-lookup"><span data-stu-id="b7147-116">In the previous example, if you declare an instance by using `Dim testClass as testClass = Nothing`, the compiler treats a call to `testClass.sayHello()` as an access of the method through the class name, and no warning occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7147-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7147-117">See also</span></span>

- [<span data-ttu-id="b7147-118">Shared</span><span class="sxs-lookup"><span data-stu-id="b7147-118">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="b7147-119">Portée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7147-119">Scope in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
