---
title: using static, directive - Référence C#
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 55847aceb9fdf032ba533b82ee59be53761fa2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712947"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="3860b-102">using static, directive (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3860b-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="3860b-103">La directive `using static` désigne un type dont vous pouvez accéder aux membres statiques et aux types imbriqués sans spécifier de nom de type.</span><span class="sxs-lookup"><span data-stu-id="3860b-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="3860b-104">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="3860b-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="3860b-105">où *fully-qualified-type-name* est le nom du type dont les membres statiques et les types imbriqués peuvent être référencés sans spécifier de nom de type.</span><span class="sxs-lookup"><span data-stu-id="3860b-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="3860b-106">Si vous ne fournissez pas de nom de type complet (le nom de l’espace de noms complet avec le nom du type), C# génère l’erreur du compilateur [CS0246](../compiler-messages/cs0246.md) : "Le nom du type ou de l’espace de noms 'type/espace_de_nom' est introuvable (il manque peut-être une directive using ou une référence d’assembly).</span><span class="sxs-lookup"><span data-stu-id="3860b-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="3860b-107">La directive `using static` s’applique à tout type ayant des membres statiques (ou des types imbriqués), même s’il a également des membres d’instance.</span><span class="sxs-lookup"><span data-stu-id="3860b-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="3860b-108">Toutefois, les membres d’instance ne peuvent être appelés que par l’instance du type.</span><span class="sxs-lookup"><span data-stu-id="3860b-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="3860b-109">La directive `using static` a été introduite avec C# 6.</span><span class="sxs-lookup"><span data-stu-id="3860b-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="3860b-110">Notes </span><span class="sxs-lookup"><span data-stu-id="3860b-110">Remarks</span></span>

<span data-ttu-id="3860b-111">En général, quand vous appelez un membre statique, vous indiquez le nom du type, ainsi que le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="3860b-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="3860b-112">Entrer plusieurs fois le même nom de type pour appeler des membres du type peut produire du code détaillé et peu clair.</span><span class="sxs-lookup"><span data-stu-id="3860b-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="3860b-113">Par exemple, la définition suivante d’une classe `Circle` référence un certain nombre de membres de la classe <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="3860b-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="3860b-114">En éliminant la nécessité de référencer explicitement la classe <xref:System.Math> chaque fois qu’un membre est référencé, la directive `using static` génère du code beaucoup plus clair :</span><span class="sxs-lookup"><span data-stu-id="3860b-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="3860b-115">`using static` importe uniquement les membres statiques accessibles et les types imbriqués déclarés dans le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="3860b-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="3860b-116">Les membres hérités ne sont pas importés.</span><span class="sxs-lookup"><span data-stu-id="3860b-116">Inherited members are not imported.</span></span>  <span data-ttu-id="3860b-117">Vous pouvez importer à partir de n'importe quel type nommé avec une directive static, notamment des modules Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3860b-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="3860b-118">Si des fonctions de niveau supérieur F# apparaissent dans les métadonnées comme membres statiques d’un type nommé dont le nom est un identificateur C# valide, les fonctions F# peuvent être importées.</span><span class="sxs-lookup"><span data-stu-id="3860b-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="3860b-119">`using static` rend les méthodes d'extension déclarées dans le type spécifié disponibles pour la recherche de méthode d'extension.</span><span class="sxs-lookup"><span data-stu-id="3860b-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="3860b-120">Toutefois, les noms des méthodes d’extension ne sont pas importés dans la portée pour la référence non qualifiée dans le code.</span><span class="sxs-lookup"><span data-stu-id="3860b-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="3860b-121">Les méthodes portant le même nom et qui sont importées à partir de différents types par différentes directives `using static` dans la même unité de compilation ou le même espace de noms forment un groupe de méthodes.</span><span class="sxs-lookup"><span data-stu-id="3860b-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="3860b-122">La résolution de surcharge au sein de ces groupes de méthodes suit des règles C# normales.</span><span class="sxs-lookup"><span data-stu-id="3860b-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="3860b-123"> Exemple</span><span class="sxs-lookup"><span data-stu-id="3860b-123">Example</span></span>

<span data-ttu-id="3860b-124">L’exemple suivant utilise la directive `using static` pour que les membres statiques des classes <xref:System.Console>, <xref:System.Math> et <xref:System.String> soient disponibles sans que vous ayez à spécifier leur nom de type.</span><span class="sxs-lookup"><span data-stu-id="3860b-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="3860b-125">Dans cet exemple, la directive `using static` aurait également pu être appliquée au type <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="3860b-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="3860b-126">Cela aurait permis d’appeler la méthode <xref:System.Double.TryParse(System.String,System.Double@)> sans spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="3860b-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="3860b-127">Toutefois, cela crée un code moins lisible, car il est nécessaire de vérifier les instructions `using static` pour déterminer quelle méthode `TryParse` du type numérique est appelée.</span><span class="sxs-lookup"><span data-stu-id="3860b-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="3860b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3860b-128">See also</span></span>

- [<span data-ttu-id="3860b-129">en utilisant la directive</span><span class="sxs-lookup"><span data-stu-id="3860b-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="3860b-130">Référence C</span><span class="sxs-lookup"><span data-stu-id="3860b-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3860b-131">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="3860b-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3860b-132">Utilisation de Namespaces</span><span class="sxs-lookup"><span data-stu-id="3860b-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="3860b-133">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="3860b-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
