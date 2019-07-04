---
title: 'Procédure : Guide pratique pour substituer la méthode ToString - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: b12aeaeb5414d911abea4dfda654183ffa02b3e6
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398456"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="8ec5d-102">Procédure : Guide pratique pour substituer la méthode ToString (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8ec5d-102">How to: Override the ToString Method (C# Programming Guide)</span></span>

<span data-ttu-id="8ec5d-103">En C#, chaque classe ou struct hérite implicitement de la classe <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8ec5d-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="8ec5d-104">Ainsi, chaque objet en C# obtient la méthode <xref:System.Object.ToString%2A>, qui retourne une représentation sous forme de chaîne de cet objet.</span><span class="sxs-lookup"><span data-stu-id="8ec5d-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="8ec5d-105">Par exemple, toutes les variables de type `int` ont une méthode `ToString`, ce qui leur permet de retourner leur contenu sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="8ec5d-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="8ec5d-106">Quand vous créez une classe ou un struct personnalisé, vous devez substituer la méthode <xref:System.Object.ToString%2A> pour fournir des informations sur votre type au code client.</span><span class="sxs-lookup"><span data-stu-id="8ec5d-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="8ec5d-107">Pour plus d’informations sur l’utilisation de chaînes de format et d’autres types de mise en forme personnalisée avec la méthode `ToString`, consultez [Mise en forme des types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="8ec5d-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8ec5d-108">Quand vous choisissez les informations à fournir par l’intermédiaire de cette méthode, déterminez si votre classe ou struct sera utilisé par du code non fiable.</span><span class="sxs-lookup"><span data-stu-id="8ec5d-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="8ec5d-109">Veillez à ne pas fournir d’informations susceptibles d’être exploitées par du code malveillant.</span><span class="sxs-lookup"><span data-stu-id="8ec5d-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="8ec5d-110">Pour substituer la méthode `ToString` dans votre classe ou struct :</span><span class="sxs-lookup"><span data-stu-id="8ec5d-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="8ec5d-111">Déclarez une méthode `ToString` avec les modificateurs et le type de retour suivants :</span><span class="sxs-lookup"><span data-stu-id="8ec5d-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="8ec5d-112">Implémentez la méthode pour qu’elle retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="8ec5d-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="8ec5d-113">L’exemple suivant retourne le nom de la classe en plus des données propres à une instance particulière de la classe.</span><span class="sxs-lookup"><span data-stu-id="8ec5d-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="8ec5d-114">Vous pouvez tester la méthode `ToString` comme illustré dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="8ec5d-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="8ec5d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ec5d-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="8ec5d-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8ec5d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8ec5d-117">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="8ec5d-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="8ec5d-118">Chaînes</span><span class="sxs-lookup"><span data-stu-id="8ec5d-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
- [<span data-ttu-id="8ec5d-119">string</span><span class="sxs-lookup"><span data-stu-id="8ec5d-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)
- [<span data-ttu-id="8ec5d-120">override</span><span class="sxs-lookup"><span data-stu-id="8ec5d-120">override</span></span>](../../../csharp/language-reference/keywords/override.md)
- [<span data-ttu-id="8ec5d-121">virtual</span><span class="sxs-lookup"><span data-stu-id="8ec5d-121">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
- [<span data-ttu-id="8ec5d-122">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="8ec5d-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
