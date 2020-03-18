---
title: protected internal - Référence C#
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713194"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="67220-102">protected internal (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="67220-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="67220-103">La combinaison de mots clés `protected internal` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="67220-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="67220-104">Un membre interne protégé est accessible depuis l’assembly actif ou depuis des types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="67220-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="67220-105">Pour obtenir une comparaison de `protected internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="67220-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="67220-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="67220-106">Example</span></span>

<span data-ttu-id="67220-107">Un membre interne protégé d’une classe de base est accessible depuis n’importe quel type au sein de son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="67220-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="67220-108">Il est également accessible dans une classe dérivée qui se trouve dans un autre assembly seulement si l’accès s’effectue via une variable du type de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="67220-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="67220-109">Prenons l’exemple de l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="67220-109">For example, consider the following code segment:</span></span>

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="67220-110">Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="67220-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="67220-111">Le premier fichier contient une classe de base publique, `BaseClass`, et une autre classe, `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="67220-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="67220-112">`BaseClass` possède un membre interne protégé, `myValue`, à laquelle le type `TestAccess` accède.</span><span class="sxs-lookup"><span data-stu-id="67220-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="67220-113">Dans le deuxième fichier, une tentative d’accès à `myValue` via une instance de `BaseClass` génère une erreur, tandis qu’un accès à ce membre via une instance d’une classe dérivée, `DerivedClass`, réussit.</span><span class="sxs-lookup"><span data-stu-id="67220-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="67220-114">Les membres de struct ne peuvent pas être `protected internal`, car le struct ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="67220-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="67220-115">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="67220-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="67220-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67220-116">See also</span></span>

- [<span data-ttu-id="67220-117">Référence C</span><span class="sxs-lookup"><span data-stu-id="67220-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="67220-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="67220-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="67220-119">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="67220-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="67220-120">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="67220-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="67220-121">Niveaux d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="67220-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="67220-122">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="67220-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="67220-123">public</span><span class="sxs-lookup"><span data-stu-id="67220-123">public</span></span>](public.md)
- [<span data-ttu-id="67220-124">Privé</span><span class="sxs-lookup"><span data-stu-id="67220-124">private</span></span>](private.md)
- [<span data-ttu-id="67220-125">Interne</span><span class="sxs-lookup"><span data-stu-id="67220-125">internal</span></span>](internal.md)
- <span data-ttu-id="67220-126">[Problèmes de sécurité pour les mots clés virtuels internes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="67220-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
