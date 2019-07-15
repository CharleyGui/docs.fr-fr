---
title: internal - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 9cfbea03a305dd17c07f549901bc91be0e05b792
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661168"
---
# <a name="internal-c-reference"></a><span data-ttu-id="24845-102">internal (référence C#)</span><span class="sxs-lookup"><span data-stu-id="24845-102">internal (C# Reference)</span></span>
<span data-ttu-id="24845-103">Le mot clé `internal` est un [modificateur d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) pour les types et les membres de type.</span><span class="sxs-lookup"><span data-stu-id="24845-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="24845-104">Cette page traite de l’accès `internal`.</span><span class="sxs-lookup"><span data-stu-id="24845-104">This page covers `internal` access.</span></span> <span data-ttu-id="24845-105">Le mot clé `internal` fait également partie du modificateur d’accès [`protected internal`](./protected-internal.md).</span><span class="sxs-lookup"><span data-stu-id="24845-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="24845-106">Les types et les membres internes (internal) sont accessibles uniquement dans les fichiers d’un même assembly, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="24845-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="24845-107">Pour obtenir une comparaison de `internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) et [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="24845-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="24845-108">Pour plus d'informations sur les assemblys, consultez [Aassemblys dans .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="24845-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="24845-109">L’accès interne est fréquemment utilisé lors du développement basé sur les composants, car il permet à un groupe de composants de collaborer de façon privée sans être exposés au reste du code de l’application.</span><span class="sxs-lookup"><span data-stu-id="24845-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="24845-110">Par exemple, un framework de création d’interfaces graphiques utilisateur peut fournir les classes `Control` et `Form` qui coopèrent en utilisant des membres ayant un accès interne.</span><span class="sxs-lookup"><span data-stu-id="24845-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="24845-111">Étant donné que ces membres sont internes, ils ne sont pas exposés au code qui utilise le framework.</span><span class="sxs-lookup"><span data-stu-id="24845-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="24845-112">Le fait de référencer un type ou un membre avec accès interne en dehors de l’assembly dans lequel il a été défini constitue une erreur.</span><span class="sxs-lookup"><span data-stu-id="24845-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24845-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="24845-113">Example</span></span>  
 <span data-ttu-id="24845-114">Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="24845-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="24845-115">Le premier fichier contient la classe de base interne `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="24845-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="24845-116">Dans le deuxième fichier, une tentative d’instanciation de `BaseClass` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="24845-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="24845-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="24845-117">Example</span></span>  
 <span data-ttu-id="24845-118">Dans cet exemple, utilisez les mêmes fichiers que vous avez utilisés dans l’exemple 1, et remplacez le niveau d’accessibilité `BaseClass` par `public`.</span><span class="sxs-lookup"><span data-stu-id="24845-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="24845-119">Remplacez également le niveau d’accessibilité du membre `intM` par `internal`.</span><span class="sxs-lookup"><span data-stu-id="24845-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="24845-120">Dans ce cas, vous pouvez instancier la classe, mais vous ne pouvez pas accéder au membre interne.</span><span class="sxs-lookup"><span data-stu-id="24845-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="24845-121">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="24845-121">C# Language Specification</span></span>  

<span data-ttu-id="24845-122">Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="24845-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="24845-123">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="24845-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="24845-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24845-124">See also</span></span>

- [<span data-ttu-id="24845-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="24845-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="24845-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="24845-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="24845-127">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="24845-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="24845-128">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="24845-128">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="24845-129">Niveaux d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="24845-129">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="24845-130">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="24845-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="24845-131">public</span><span class="sxs-lookup"><span data-stu-id="24845-131">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="24845-132">private</span><span class="sxs-lookup"><span data-stu-id="24845-132">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="24845-133">protected</span><span class="sxs-lookup"><span data-stu-id="24845-133">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
