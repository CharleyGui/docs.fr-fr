---
title: Comment déclarer et utiliser des propriétés en lecture/ C# écriture-Guide de programmation
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 5b880cfc3ace197a3bad2f707cf55543dbe7b78e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714930"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="46a70-102">Comment déclarer et utiliser les propriétés en lecture/C# écriture (Guide de programmation)</span><span class="sxs-lookup"><span data-stu-id="46a70-102">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="46a70-103">Les propriétés offrent la commodité des membres de données publics sans les risques liés à un accès non protégé, non contrôlé et non vérifié aux données d’un objet.</span><span class="sxs-lookup"><span data-stu-id="46a70-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="46a70-104">Cela se fait au moyen d’*accesseurs*, lesquels sont des méthodes spéciales qui affectent et récupèrent des valeurs du membre de données sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="46a70-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="46a70-105">L’accesseur [set](../../language-reference/keywords/set.md) permet aux membres de données d’être affectés, et l’accesseur [get](../../language-reference/keywords/get.md) récupère des valeurs de membres de données.</span><span class="sxs-lookup"><span data-stu-id="46a70-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="46a70-106">L’exemple suivant montre une classe `Person` qui possède deux propriétés : `Name` (string) et `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="46a70-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="46a70-107">Étant donné que les deux propriétés fournissent des accesseurs `get` et `set`, elles sont considérées comme des propriétés en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="46a70-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46a70-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="46a70-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="46a70-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="46a70-109">Robust Programming</span></span>  
 <span data-ttu-id="46a70-110">Dans l’exemple précédent, les propriétés `Name` et `Age` sont [publiques](../../language-reference/keywords/public.md), et incluent un accesseur `get` et un accesseur `set`.</span><span class="sxs-lookup"><span data-stu-id="46a70-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="46a70-111">Cela permet à n’importe quel objet de lire et d’écrire ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="46a70-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="46a70-112">Toutefois, il est parfois souhaitable d’exclure l’un des accesseurs.</span><span class="sxs-lookup"><span data-stu-id="46a70-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="46a70-113">L’omission de l’accesseur `set`, par exemple, met la propriété en lecture seule :</span><span class="sxs-lookup"><span data-stu-id="46a70-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="46a70-114">Vous pouvez également exposer publiquement un accesseur mais rendre l’autre private ou protected.</span><span class="sxs-lookup"><span data-stu-id="46a70-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="46a70-115">Pour plus d’informations, consultez [Accessibilité de l’accesseur asymétrique](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="46a70-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="46a70-116">Une fois les propriétés déclarées, vous pouvez les utiliser comme s’il s’agissait de champs de la classe.</span><span class="sxs-lookup"><span data-stu-id="46a70-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="46a70-117">Cela permet une syntaxe très naturelle pour obtenir ou définir la valeur d’une propriété, comme dans les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="46a70-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="46a70-118">Notez qu’une variable `value` spéciale est disponible dans la méthode `set` d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="46a70-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="46a70-119">Cette variable contient la valeur que l’utilisateur a spécifiée, par exemple :</span><span class="sxs-lookup"><span data-stu-id="46a70-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="46a70-120">Notez la syntaxe correcte pour incrémenter la propriété `Age` sur un objet `Person` :</span><span class="sxs-lookup"><span data-stu-id="46a70-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="46a70-121">Si des méthodes `set` et `get` distinctes ont été utilisées pour modeler des propriétés, le code équivalent peut avoir la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="46a70-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="46a70-122">La méthode `ToString` est substituée dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="46a70-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="46a70-123">Vous pouvez remarquer que `ToString` n’est pas utilisée de façon explicite dans le programme.</span><span class="sxs-lookup"><span data-stu-id="46a70-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="46a70-124">Elle est appelée par défaut par les appels `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="46a70-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a70-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46a70-125">See also</span></span>

- [<span data-ttu-id="46a70-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="46a70-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="46a70-127">Propriétés</span><span class="sxs-lookup"><span data-stu-id="46a70-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="46a70-128">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="46a70-128">Classes and Structs</span></span>](./index.md)
