---
title: Structures - Guide de programmation C#
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 063d7e3b68fbe6c01ff0df4ae935fec5af6f6891
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743836"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="29e7a-102">Structures (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="29e7a-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="29e7a-103">Les structs sont définis à l’aide du mot clé [struct](../../language-reference/keywords/struct.md), par exemple :</span><span class="sxs-lookup"><span data-stu-id="29e7a-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
<span data-ttu-id="29e7a-104">Les structs partagent quasiment la même syntaxe que les classes.</span><span class="sxs-lookup"><span data-stu-id="29e7a-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="29e7a-105">Le nom du struct doit être un [nom d’identificateur](../inside-a-program/identifier-names.md) C# valide.</span><span class="sxs-lookup"><span data-stu-id="29e7a-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="29e7a-106">Les structs sont plus limités que les classes des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="29e7a-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="29e7a-107">Au sein d’une déclaration de struct, les champs ne peuvent pas être initialisés à moins d’être déclarés comme étant de type const ou static.</span><span class="sxs-lookup"><span data-stu-id="29e7a-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="29e7a-108">Un struct ne peut pas déclarer de constructeur sans paramètre ni de finaliseur.</span><span class="sxs-lookup"><span data-stu-id="29e7a-108">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="29e7a-109">Les structs sont copiés lors de l'assignation.</span><span class="sxs-lookup"><span data-stu-id="29e7a-109">Structs are copied on assignment.</span></span> <span data-ttu-id="29e7a-110">Lorsqu'un struct est assigné à une nouvelle variable, toutes les données sont copiées et les modifications apportées à la nouvelle copie ne changent pas les données de la copie d'origine.</span><span class="sxs-lookup"><span data-stu-id="29e7a-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="29e7a-111">Il est important de vous en souvenir quand vous utilisez des collections de types valeur telles que `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="29e7a-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="29e7a-112">Les structs sont des types valeur, contrairement aux classes, qui sont des types référence.</span><span class="sxs-lookup"><span data-stu-id="29e7a-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="29e7a-113">Contrairement aux classes, il est possible d’instancier les structs sans avoir recours à un opérateur `new`.</span><span class="sxs-lookup"><span data-stu-id="29e7a-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="29e7a-114">Les structs peuvent déclarer des constructeurs qui ont des paramètres.</span><span class="sxs-lookup"><span data-stu-id="29e7a-114">Structs can declare constructors that have parameters.</span></span>
- <span data-ttu-id="29e7a-115">Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe.</span><span class="sxs-lookup"><span data-stu-id="29e7a-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="29e7a-116">Tous les structs héritent directement de <xref:System.ValueType>, qui hérite de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="29e7a-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="29e7a-117">Un struct peut implémenter des interfaces.</span><span class="sxs-lookup"><span data-stu-id="29e7a-117">A struct can implement interfaces.</span></span>
- <span data-ttu-id="29e7a-118">Un struct ne peut pas être `null`, et une variable de struct ne peut pas se voir assigner `null`, sauf si elle est déclarée en tant que type nullable.</span><span class="sxs-lookup"><span data-stu-id="29e7a-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable type.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="29e7a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29e7a-119">See also</span></span>

- [<span data-ttu-id="29e7a-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="29e7a-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="29e7a-121">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="29e7a-121">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="29e7a-122">Classes</span><span class="sxs-lookup"><span data-stu-id="29e7a-122">Classes</span></span>](classes.md)
- [<span data-ttu-id="29e7a-123">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="29e7a-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="29e7a-124">Noms d’identificateur</span><span class="sxs-lookup"><span data-stu-id="29e7a-124">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="29e7a-125">Utilisation de structs</span><span class="sxs-lookup"><span data-stu-id="29e7a-125">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="29e7a-126">Guide pratique pour différencier le passage d’un struct et le passage d’une référence de classe à une méthode</span><span class="sxs-lookup"><span data-stu-id="29e7a-126">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
