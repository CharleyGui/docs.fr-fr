---
title: Noms d’identificateurs
description: Découvrez les règles relatives aux noms d’identificateurs valides dans le langage de programmation C#.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673366"
---
# <a name="identifier-names"></a><span data-ttu-id="3d788-103">Noms d’identificateurs</span><span class="sxs-lookup"><span data-stu-id="3d788-103">Identifier names</span></span>

<span data-ttu-id="3d788-104">Un **identificateur** est le nom que vous assignez à un type (classe, interface, struct, délégué ou enum), un membre, une variable ou un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3d788-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="3d788-105">Les identificateurs valides doivent suivre les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="3d788-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="3d788-106">Les identificateurs doivent commencer par une lettre ou par `_`.</span><span class="sxs-lookup"><span data-stu-id="3d788-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="3d788-107">Les identificateurs peuvent contenir des lettres Unicode, des nombres décimaux, des caractères de connexion Unicode, des caractères de combinaison Unicode ou des caractères de mise en forme Unicode.</span><span class="sxs-lookup"><span data-stu-id="3d788-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="3d788-108">Pour plus d’informations sur les catégories Unicode, consultez la [Base de données des catégories Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="3d788-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="3d788-109">Vous pouvez déclarer des identificateurs qui correspondent à des mots clés C# en utilisant le préfixe `@` sur l’identificateur.</span><span class="sxs-lookup"><span data-stu-id="3d788-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="3d788-110">`@` ne fait pas partie du nom de l’identificateur.</span><span class="sxs-lookup"><span data-stu-id="3d788-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="3d788-111">Par exemple, `@if` déclare un identificateur nommé `if`.</span><span class="sxs-lookup"><span data-stu-id="3d788-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="3d788-112">Ces [identificateurs textuels](../../language-reference/tokens/verbatim.md) sont destinés principalement à assurer l’interopérabilité avec les identificateurs déclarés dans d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="3d788-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="3d788-113">Pour une définition complète des identificateurs valides, consultez la rubrique [Identificateurs dans la spécification du langage C#](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span><span class="sxs-lookup"><span data-stu-id="3d788-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="3d788-114">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="3d788-114">Naming conventions</span></span>

<span data-ttu-id="3d788-115">En plus des règles, un certain nombre de [conventions de nommage](../../../standard/design-guidelines/naming-guidelines.md) des identificateurs sont utilisées dans les API .NET.</span><span class="sxs-lookup"><span data-stu-id="3d788-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="3d788-116">Par convention, les programmes C# utilisent `PascalCase` pour les noms de types, les espaces de noms et tous les membres publics.</span><span class="sxs-lookup"><span data-stu-id="3d788-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="3d788-117">De plus, les conventions suivantes sont communément respectées :</span><span class="sxs-lookup"><span data-stu-id="3d788-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="3d788-118">Les noms d’interfaces commencent par un `I` majuscule.</span><span class="sxs-lookup"><span data-stu-id="3d788-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="3d788-119">Les types d’attribut finissent par le mot `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="3d788-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="3d788-120">Les types enum utilisent un nom singulier pour les non-indicateurs et un nom pluriel pour les indicateurs.</span><span class="sxs-lookup"><span data-stu-id="3d788-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="3d788-121">Les identificateurs ne doivent pas contenir deux caractères `_` consécutifs.</span><span class="sxs-lookup"><span data-stu-id="3d788-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="3d788-122">Ces noms sont réservés aux identificateurs générés par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="3d788-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3d788-123">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3d788-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d788-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d788-124">See also</span></span>

- [<span data-ttu-id="3d788-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3d788-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3d788-126">À l'intérieur d'un programme C#</span><span class="sxs-lookup"><span data-stu-id="3d788-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="3d788-127">Référence C</span><span class="sxs-lookup"><span data-stu-id="3d788-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3d788-128">Classes</span><span class="sxs-lookup"><span data-stu-id="3d788-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="3d788-129">Types de structure</span><span class="sxs-lookup"><span data-stu-id="3d788-129">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="3d788-130">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="3d788-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="3d788-131">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3d788-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="3d788-132">Délégués</span><span class="sxs-lookup"><span data-stu-id="3d788-132">Delegates</span></span>](../delegates/index.md)
