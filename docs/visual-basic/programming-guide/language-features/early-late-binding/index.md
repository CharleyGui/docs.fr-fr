---
title: Liaison anticipée et liaison tardive
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: ce74498225fb7947c92f2f4f61ec46e6b2594151
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086008"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="409b2-102">Liaison anticipée et liaison tardive (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="409b2-102">Early and Late Binding (Visual Basic)</span></span>

<span data-ttu-id="409b2-103">Le compilateur Visual Basic exécute un processus appelé `binding` lorsqu’un objet est assigné à une variable objet.</span><span class="sxs-lookup"><span data-stu-id="409b2-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="409b2-104">Un objet est dit *à liaison anticipée* lorsqu’il est affecté à une variable déclarée comme étant d’un type d’objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="409b2-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="409b2-105">Les objets à liaison anticipée permettent au compilateur d’allouer de la mémoire et d’effectuer d’autres optimisations avant l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="409b2-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="409b2-106">Par exemple, le fragment de code suivant déclare une variable de type <xref:System.IO.FileStream> :</span><span class="sxs-lookup"><span data-stu-id="409b2-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="409b2-107">Étant donné que <xref:System.IO.FileStream> est un type d’objet spécifique, l’instance affectée à `FS` est à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="409b2-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="409b2-108">Par opposition, un objet est dit *à liaison tardive* lorsqu’il est affecté à une variable déclarée comme étant du type `Object`.</span><span class="sxs-lookup"><span data-stu-id="409b2-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="409b2-109">Les objets de ce type peuvent contenir des références à n’importe quel objet, mais ne présentent pas tous les avantages des objets à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="409b2-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="409b2-110">Par exemple, le fragment de code suivant déclare une variable objet qui contient un objet retourné par la fonction `CreateObject` :</span><span class="sxs-lookup"><span data-stu-id="409b2-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="409b2-111">Avantages de la liaison anticipée</span><span class="sxs-lookup"><span data-stu-id="409b2-111">Advantages of Early Binding</span></span>  

 <span data-ttu-id="409b2-112">Utilisez des objets à liaison anticipée chaque fois que c’est possible, car ils permettent au compilateur d’effectuer d’importantes optimisations qui génèrent des applications plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="409b2-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="409b2-113">Les objets à liaison anticipée sont considérablement plus rapides que les objets à liaison tardive et rendent votre code plus facile à lire et à gérer en indiquant exactement quels types d’objets sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="409b2-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="409b2-114">L’un des avantages de la liaison précoce est qu’elle permet des fonctionnalités utiles telles que la saisie semi-automatique du code et l’aide dynamique, car l’environnement de développement intégré (IDE) de Visual Studio peut déterminer exactement le type d’objet avec lequel vous travaillez lorsque vous modifiez le code.</span><span class="sxs-lookup"><span data-stu-id="409b2-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="409b2-115">Elle réduit le nombre et la gravité des erreurs d’exécution, car elle permet au compilateur de signaler des erreurs à la compilation du programme.</span><span class="sxs-lookup"><span data-stu-id="409b2-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="409b2-116">La liaison tardive ne peut être utilisée que pour accéder aux membres de type déclarés comme `Public`.</span><span class="sxs-lookup"><span data-stu-id="409b2-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="409b2-117">L’accès aux membres déclarés comme `Friend` ou `Protected Friend` provoque une erreur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="409b2-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409b2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="409b2-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="409b2-119">Durée de vie d’un objet : création et destruction des objets</span><span class="sxs-lookup"><span data-stu-id="409b2-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="409b2-120">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="409b2-120">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
