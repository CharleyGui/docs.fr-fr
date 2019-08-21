---
title: 'Opérateur :: - Référence C#'
ms.custom: seodec18
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2aceb51747708b12fb3059b097b72206c78a9d5d
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971243"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d836c-102">Opérateur :: (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d836c-102">:: operator (C# reference)</span></span>

<span data-ttu-id="d836c-103">Utilisez le qualificateur d’alias d’espace de noms `::` pour accéder aux membres d’un espace de noms avec alias.</span><span class="sxs-lookup"><span data-stu-id="d836c-103">Use the namespace alias qualifier `::` to access members of an aliased namespace.</span></span> <span data-ttu-id="d836c-104">Vous utilisez le qualificateur `::` entre deux identificateurs.</span><span class="sxs-lookup"><span data-stu-id="d836c-104">You use the `::` qualifier between two identifiers.</span></span> <span data-ttu-id="d836c-105">L’identificateur de gauche peut être un des alias suivants :</span><span class="sxs-lookup"><span data-stu-id="d836c-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="d836c-106">Un alias d’espace de noms créé avec la [directive using alias](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="d836c-106">A namespace alias created with the [using alias directive](../keywords/using-directive.md):</span></span>
  
  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="d836c-107">Un [alias externe](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="d836c-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="d836c-108">L’alias `global`, qui est l’alias d’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="d836c-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="d836c-109">L’espace de noms global est l’espace de noms qui contient des espaces de noms et des types qui ne sont pas déclarés dans un espace de noms nommé.</span><span class="sxs-lookup"><span data-stu-id="d836c-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="d836c-110">Quand il est utilisé avec le qualificateur `::`, l’alias `global` référence toujours l’espace de noms global, même si l’alias d’espace de noms `global` défini par l’utilisateur est présent.</span><span class="sxs-lookup"><span data-stu-id="d836c-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>
  
  <span data-ttu-id="d836c-111">L’exemple suivant utilise l’alias `global` pour accéder à l’espace de noms .NET <xref:System>, qui est un membre de l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="d836c-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="d836c-112">Sans l’alias `global`, l’accès se ferait à l’espace de noms `System` défini par l’utilisateur, qui est un membre de l’espace de noms `MyCompany.MyProduct` :</span><span class="sxs-lookup"><span data-stu-id="d836c-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }
  
      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```
  
  > [!NOTE]
  > <span data-ttu-id="d836c-113">Le mot clé `global` est l’alias d’espace de noms global seulement quand il s’agit de l’identificateur de gauche du qualificateur `::`.</span><span class="sxs-lookup"><span data-stu-id="d836c-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="d836c-114">Vous pouvez également utiliser l’[opérateur d’accès aux membres `.`](member-access-operators.md#member-access-operator-) pour accéder aux membres d’un espace de noms avec alias.</span><span class="sxs-lookup"><span data-stu-id="d836c-114">You can also use the [member access `.` operator](member-access-operators.md#member-access-operator-) to access members of an aliased namespace.</span></span> <span data-ttu-id="d836c-115">Cependant, l’opérateur `.` est également utilisé pour accéder aux membres d’un type.</span><span class="sxs-lookup"><span data-stu-id="d836c-115">However, the `.` operator is also used to access members of a type.</span></span> <span data-ttu-id="d836c-116">Le qualificateur `::` garantit que son identificateur de gauche référence toujours un alias d’espace de noms, même s’il existe un type ou un espace de noms portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="d836c-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d836c-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d836c-117">C# language specification</span></span>

<span data-ttu-id="d836c-118">Pour plus d’informations, consultez la section [Qualificateurs d’alias d’espace de noms](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d836c-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d836c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d836c-119">See also</span></span>

- [<span data-ttu-id="d836c-120">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="d836c-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d836c-121">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="d836c-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="d836c-122">Utilisation des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="d836c-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
