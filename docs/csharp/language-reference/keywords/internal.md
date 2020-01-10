---
title: internal - Référence C#
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: db653d0ed7f4835348484242b03392a8955c6392
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713426"
---
# <a name="internal-c-reference"></a><span data-ttu-id="a72b4-102">internal (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a72b4-102">internal (C# Reference)</span></span>
<span data-ttu-id="a72b4-103">Le mot clé `internal` est un [modificateur d’accès](./access-modifiers.md) pour les types et les membres de type.</span><span class="sxs-lookup"><span data-stu-id="a72b4-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="a72b4-104">Cette page traite de l’accès `internal`.</span><span class="sxs-lookup"><span data-stu-id="a72b4-104">This page covers `internal` access.</span></span> <span data-ttu-id="a72b4-105">Le mot clé `internal` fait également partie du modificateur d’accès [`protected internal`](./protected-internal.md).</span><span class="sxs-lookup"><span data-stu-id="a72b4-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="a72b4-106">Les types et les membres internes (internal) sont accessibles uniquement dans les fichiers d’un même assembly, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a72b4-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="a72b4-107">Pour obtenir une comparaison de `internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](./accessibility-levels.md) et [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="a72b4-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="a72b4-108">Pour plus d'informations sur les assemblys, consultez [Aassemblys dans .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="a72b4-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="a72b4-109">L’accès interne est fréquemment utilisé lors du développement basé sur les composants, car il permet à un groupe de composants de collaborer de façon privée sans être exposés au reste du code de l’application.</span><span class="sxs-lookup"><span data-stu-id="a72b4-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="a72b4-110">Par exemple, un framework de création d’interfaces graphiques utilisateur peut fournir les classes `Control` et `Form` qui coopèrent en utilisant des membres ayant un accès interne.</span><span class="sxs-lookup"><span data-stu-id="a72b4-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="a72b4-111">Étant donné que ces membres sont internes, ils ne sont pas exposés au code qui utilise le framework.</span><span class="sxs-lookup"><span data-stu-id="a72b4-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="a72b4-112">Le fait de référencer un type ou un membre avec accès interne en dehors de l’assembly dans lequel il a été défini constitue une erreur.</span><span class="sxs-lookup"><span data-stu-id="a72b4-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a72b4-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="a72b4-113">Example</span></span>  
 <span data-ttu-id="a72b4-114">Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="a72b4-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="a72b4-115">Le premier fichier contient la classe de base interne `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="a72b4-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="a72b4-116">Dans le deuxième fichier, une tentative d’instanciation de `BaseClass` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="a72b4-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a72b4-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="a72b4-117">Example</span></span>  
 <span data-ttu-id="a72b4-118">Dans cet exemple, utilisez les mêmes fichiers que vous avez utilisés dans l’exemple 1, et remplacez le niveau d’accessibilité `BaseClass` par `public`.</span><span class="sxs-lookup"><span data-stu-id="a72b4-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="a72b4-119">Remplacez également le niveau d’accessibilité du membre `intM` par `internal`.</span><span class="sxs-lookup"><span data-stu-id="a72b4-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="a72b4-120">Dans ce cas, vous pouvez instancier la classe, mais vous ne pouvez pas accéder au membre interne.</span><span class="sxs-lookup"><span data-stu-id="a72b4-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="a72b4-121">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a72b4-121">C# Language Specification</span></span>  

<span data-ttu-id="a72b4-122">Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="a72b4-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="a72b4-123">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="a72b4-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a72b4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a72b4-124">See also</span></span>

- [<span data-ttu-id="a72b4-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a72b4-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a72b4-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a72b4-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a72b4-127">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a72b4-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="a72b4-128">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="a72b4-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="a72b4-129">Niveaux d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="a72b4-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="a72b4-130">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="a72b4-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="a72b4-131">public</span><span class="sxs-lookup"><span data-stu-id="a72b4-131">public</span></span>](./public.md)
- [<span data-ttu-id="a72b4-132">private</span><span class="sxs-lookup"><span data-stu-id="a72b4-132">private</span></span>](./private.md)
- [<span data-ttu-id="a72b4-133">protected</span><span class="sxs-lookup"><span data-stu-id="a72b4-133">protected</span></span>](./protected.md)
