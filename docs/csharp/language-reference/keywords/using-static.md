---
description: using static, directive - Référence C#
title: using static, directive - Référence C#
ms.date: 03/10/2017
f1_keywords:
- using-static_CSharpKeyword
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: d117d4423a2f7c782cd6365a73e6c18298d89abc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162230"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="c37f9-103">using static, directive (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c37f9-103">using static directive (C# Reference)</span></span>

<span data-ttu-id="c37f9-104">La directive `using static` désigne un type dont vous pouvez accéder aux membres statiques et aux types imbriqués sans spécifier de nom de type.</span><span class="sxs-lookup"><span data-stu-id="c37f9-104">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="c37f9-105">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c37f9-105">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="c37f9-106">où *fully-qualified-type-name* est le nom du type dont les membres statiques et les types imbriqués peuvent être référencés sans spécifier de nom de type.</span><span class="sxs-lookup"><span data-stu-id="c37f9-106">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="c37f9-107">Si vous ne fournissez pas de nom de type complet (le nom de l’espace de noms complet avec le nom du type), C# génère l’erreur du compilateur [CS0246](../compiler-messages/cs0246.md) : "Le nom du type ou de l’espace de noms 'type/espace_de_nom' est introuvable (il manque peut-être une directive using ou une référence d’assembly).</span><span class="sxs-lookup"><span data-stu-id="c37f9-107">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="c37f9-108">La directive `using static` s’applique à tout type ayant des membres statiques (ou des types imbriqués), même s’il a également des membres d’instance.</span><span class="sxs-lookup"><span data-stu-id="c37f9-108">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="c37f9-109">Toutefois, les membres d’instance ne peuvent être appelés que par l’instance du type.</span><span class="sxs-lookup"><span data-stu-id="c37f9-109">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="c37f9-110">La directive `using static` a été introduite avec C# 6.</span><span class="sxs-lookup"><span data-stu-id="c37f9-110">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="c37f9-111">Notes </span><span class="sxs-lookup"><span data-stu-id="c37f9-111">Remarks</span></span>

<span data-ttu-id="c37f9-112">En général, quand vous appelez un membre statique, vous indiquez le nom du type, ainsi que le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="c37f9-112">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="c37f9-113">Entrer plusieurs fois le même nom de type pour appeler des membres du type peut produire du code détaillé et peu clair.</span><span class="sxs-lookup"><span data-stu-id="c37f9-113">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="c37f9-114">Par exemple, la définition suivante d’une classe `Circle` référence un certain nombre de membres de la classe <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="c37f9-114">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="c37f9-115">En éliminant la nécessité de référencer explicitement la classe <xref:System.Math> chaque fois qu’un membre est référencé, la directive `using static` génère du code beaucoup plus clair :</span><span class="sxs-lookup"><span data-stu-id="c37f9-115">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="c37f9-116">`using static` importe uniquement les membres statiques accessibles et les types imbriqués déclarés dans le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="c37f9-116">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="c37f9-117">Les membres hérités ne sont pas importés.</span><span class="sxs-lookup"><span data-stu-id="c37f9-117">Inherited members are not imported.</span></span>  <span data-ttu-id="c37f9-118">Vous pouvez importer à partir de n'importe quel type nommé avec une directive static, notamment des modules Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c37f9-118">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="c37f9-119">Si des fonctions de niveau supérieur F# apparaissent dans les métadonnées comme membres statiques d’un type nommé dont le nom est un identificateur C# valide, les fonctions F# peuvent être importées.</span><span class="sxs-lookup"><span data-stu-id="c37f9-119">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="c37f9-120">`using static` rend les méthodes d'extension déclarées dans le type spécifié disponibles pour la recherche de méthode d'extension.</span><span class="sxs-lookup"><span data-stu-id="c37f9-120">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="c37f9-121">Toutefois, les noms des méthodes d’extension ne sont pas importés dans la portée pour la référence non qualifiée dans le code.</span><span class="sxs-lookup"><span data-stu-id="c37f9-121">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="c37f9-122">Les méthodes portant le même nom et qui sont importées à partir de différents types par différentes directives `using static` dans la même unité de compilation ou le même espace de noms forment un groupe de méthodes.</span><span class="sxs-lookup"><span data-stu-id="c37f9-122">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="c37f9-123">La résolution de surcharge au sein de ces groupes de méthodes suit des règles C# normales.</span><span class="sxs-lookup"><span data-stu-id="c37f9-123">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="c37f9-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c37f9-124">Example</span></span>

<span data-ttu-id="c37f9-125">L’exemple suivant utilise la directive `using static` pour que les membres statiques des classes <xref:System.Console>, <xref:System.Math> et <xref:System.String> soient disponibles sans que vous ayez à spécifier leur nom de type.</span><span class="sxs-lookup"><span data-stu-id="c37f9-125">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="c37f9-126">Dans cet exemple, la directive `using static` aurait également pu être appliquée au type <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="c37f9-126">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="c37f9-127">Cela aurait permis d’appeler la méthode <xref:System.Double.TryParse(System.String,System.Double@)> sans spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="c37f9-127">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="c37f9-128">Toutefois, cela crée un code moins lisible, puisqu’il est nécessaire de vérifier les `using static` directives pour déterminer la méthode du type numérique qui `TryParse` est appelée.</span><span class="sxs-lookup"><span data-stu-id="c37f9-128">However, this creates less readable code, since it becomes necessary to check the `using static` directives to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="c37f9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c37f9-129">See also</span></span>

- [<span data-ttu-id="c37f9-130">using, directive</span><span class="sxs-lookup"><span data-stu-id="c37f9-130">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="c37f9-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="c37f9-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c37f9-132">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="c37f9-132">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c37f9-133">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="c37f9-133">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="c37f9-134">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="c37f9-134">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
