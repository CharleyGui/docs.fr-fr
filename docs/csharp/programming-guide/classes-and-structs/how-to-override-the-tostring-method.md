---
title: Comment substituer la méthode ToString-Guide de programmation C#
description: Découvrez comment substituer la méthode ToString en C#. Chaque classe ou struct hérite de l’objet et obtient ToString, qui retourne une représentation sous forme de chaîne de cet objet.
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 65b34b485d4b90173a4c956dd0ebaaa590a0c7c9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865006"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="f76de-104">Comment substituer la méthode ToString (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f76de-104">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="f76de-105">En C#, chaque classe ou struct hérite implicitement de la classe <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f76de-105">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="f76de-106">Ainsi, chaque objet en C# obtient la méthode <xref:System.Object.ToString%2A>, qui retourne une représentation sous forme de chaîne de cet objet.</span><span class="sxs-lookup"><span data-stu-id="f76de-106">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="f76de-107">Par exemple, toutes les variables de type `int` ont une méthode `ToString`, ce qui leur permet de retourner leur contenu sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="f76de-107">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="f76de-108">Quand vous créez une classe ou un struct personnalisé, vous devez substituer la méthode <xref:System.Object.ToString%2A> pour fournir des informations sur votre type au code client.</span><span class="sxs-lookup"><span data-stu-id="f76de-108">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="f76de-109">Pour plus d’informations sur l’utilisation de chaînes de format et d’autres types de mise en forme personnalisée avec la méthode `ToString`, consultez [Mise en forme des types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="f76de-109">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f76de-110">Quand vous choisissez les informations à fournir par l’intermédiaire de cette méthode, déterminez si votre classe ou struct sera utilisé par du code non fiable.</span><span class="sxs-lookup"><span data-stu-id="f76de-110">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="f76de-111">Veillez à ne pas fournir d’informations susceptibles d’être exploitées par du code malveillant.</span><span class="sxs-lookup"><span data-stu-id="f76de-111">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="f76de-112">Pour substituer la méthode `ToString` dans votre classe ou struct :</span><span class="sxs-lookup"><span data-stu-id="f76de-112">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="f76de-113">Déclarez une méthode `ToString` avec les modificateurs et le type de retour suivants :</span><span class="sxs-lookup"><span data-stu-id="f76de-113">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="f76de-114">Implémentez la méthode pour qu’elle retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f76de-114">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="f76de-115">L’exemple suivant retourne le nom de la classe en plus des données propres à une instance particulière de la classe.</span><span class="sxs-lookup"><span data-stu-id="f76de-115">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="f76de-116">Vous pouvez tester la méthode `ToString` comme illustré dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="f76de-116">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="f76de-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f76de-117">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="f76de-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f76de-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f76de-119">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="f76de-119">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="f76de-120">Chaînes</span><span class="sxs-lookup"><span data-stu-id="f76de-120">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="f76de-121">string</span><span class="sxs-lookup"><span data-stu-id="f76de-121">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="f76de-122">remplacer</span><span class="sxs-lookup"><span data-stu-id="f76de-122">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="f76de-123">virtuels</span><span class="sxs-lookup"><span data-stu-id="f76de-123">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="f76de-124">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="f76de-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
