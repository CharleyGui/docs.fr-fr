---
title: 'Opérateur :: - Référence C#'
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
ms.openlocfilehash: 84c418627462f83630fe5072a0b0e2089f6588f6
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507124"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3b214-102">Opérateur :: (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3b214-102">:: operator (C# reference)</span></span>

<span data-ttu-id="3b214-103">Utilisez le nomspace `::` alias qualifier pour accéder à un membre d’un espace nom alias.</span><span class="sxs-lookup"><span data-stu-id="3b214-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="3b214-104">Vous ne `::` pouvez utiliser le qualificatif qu’entre deux identificateurs.</span><span class="sxs-lookup"><span data-stu-id="3b214-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="3b214-105">L’identificateur de gauche peut être un des alias suivants :</span><span class="sxs-lookup"><span data-stu-id="3b214-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="3b214-106">Un alias namespace créé avec une [directive alias utilisant](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="3b214-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="3b214-107">Un [alias externe](../keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="3b214-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="3b214-108">L’alias `global`, qui est l’alias d’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="3b214-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="3b214-109">L’espace de noms global est l’espace de noms qui contient des espaces de noms et des types qui ne sont pas déclarés dans un espace de noms nommé.</span><span class="sxs-lookup"><span data-stu-id="3b214-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="3b214-110">Quand il est utilisé avec le qualificateur `::`, l’alias `global` référence toujours l’espace de noms global, même si l’alias d’espace de noms `global` défini par l’utilisateur est présent.</span><span class="sxs-lookup"><span data-stu-id="3b214-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="3b214-111">L’exemple suivant utilise l’alias `global` pour accéder à l’espace de noms .NET <xref:System>, qui est un membre de l’espace de noms global.</span><span class="sxs-lookup"><span data-stu-id="3b214-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="3b214-112">Sans l’alias `global`, l’accès se ferait à l’espace de noms `System` défini par l’utilisateur, qui est un membre de l’espace de noms `MyCompany.MyProduct` :</span><span class="sxs-lookup"><span data-stu-id="3b214-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="3b214-113">Le mot clé `global` est l’alias d’espace de noms global seulement quand il s’agit de l’identificateur de gauche du qualificateur `::`.</span><span class="sxs-lookup"><span data-stu-id="3b214-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="3b214-114">Vous pouvez également utiliser le [ `.` jeton](member-access-operators.md#member-access-expression-) pour accéder à un membre d’un espace nom alias.</span><span class="sxs-lookup"><span data-stu-id="3b214-114">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="3b214-115">Cependant, `.` le jeton est également utilisé pour accéder à un membre type.</span><span class="sxs-lookup"><span data-stu-id="3b214-115">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="3b214-116">Le qualificateur `::` garantit que son identificateur de gauche référence toujours un alias d’espace de noms, même s’il existe un type ou un espace de noms portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="3b214-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3b214-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3b214-117">C# language specification</span></span>

<span data-ttu-id="3b214-118">Pour plus d’informations, consultez la section [Qualificateurs d’alias d’espace de noms](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3b214-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3b214-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b214-119">See also</span></span>

- [<span data-ttu-id="3b214-120">Référence C#</span><span class="sxs-lookup"><span data-stu-id="3b214-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3b214-121">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="3b214-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="3b214-122">Using Namespaces</span><span class="sxs-lookup"><span data-stu-id="3b214-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
