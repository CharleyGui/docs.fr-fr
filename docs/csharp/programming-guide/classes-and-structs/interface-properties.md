---
title: Propriétés d'interface - Guide de programmation C#
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626618"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="2eeaa-102">Propriétés d'interface (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2eeaa-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="2eeaa-103">Des propriétés peuvent être déclarées dans une [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="2eeaa-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="2eeaa-104">L’exemple suivant déclare un accessoir de propriété d’interface :</span><span class="sxs-lookup"><span data-stu-id="2eeaa-104">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="2eeaa-105">Les propriétés d’interface n’ont généralement pas de corps.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-105">Interface properties typically don't have a body.</span></span> <span data-ttu-id="2eeaa-106">Les accesseurs indiquent si la propriété est lue-écriture, lu-seulement, ou écrire-seulement.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-106">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="2eeaa-107">Contrairement aux classes et aux structs, déclarer les accesseurs sans corps ne déclare pas une [propriété auto-mise en œuvre.](auto-implemented-properties.md)</span><span class="sxs-lookup"><span data-stu-id="2eeaa-107">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="2eeaa-108">En commençant par le C 8.0, une interface peut définir une implémentation par défaut pour les membres, y compris les propriétés.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-108">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="2eeaa-109">Définir une implémentation par défaut pour une propriété dans une interface est rare car les interfaces peuvent ne pas définir les champs de données d’instance.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-109">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="2eeaa-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2eeaa-110">Example</span></span>

<span data-ttu-id="2eeaa-111">Dans cet exemple, l’interface `IEmployee` a une propriété en lecture-écriture, `Name`, et une propriété en lecture seule, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-111">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="2eeaa-112">La classe `Employee` implémente l’interface `IEmployee` et utilise ces deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-112">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="2eeaa-113">Le programme lit le nom d’un nouvel employé et le nombre actuel d’employés et affiche le nom de l’employé et le nombre d’employés calculé.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-113">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="2eeaa-114">Vous pouvez utiliser le nom qualifié complet de la propriété, qui fait référence à l’interface dans laquelle le membre est déclaré.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-114">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="2eeaa-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2eeaa-115">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="2eeaa-116">L’exemple précédent démontre [la mise en œuvre explicite de l’interface](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="2eeaa-116">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="2eeaa-117">Par exemple, si la classe `Employee` implémente deux interfaces, `ICitizen` et `IEmployee`, et que les deux interfaces ont la même propriété `Name`, l’implémentation de membre d’interface explicite est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-117">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="2eeaa-118">Autrement dit, la déclaration de propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="2eeaa-118">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="2eeaa-119">implémente la propriété `Name` dans l’interface `IEmployee`, alors que la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="2eeaa-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="2eeaa-120">implémente la propriété `Name` dans l’interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="2eeaa-120">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="2eeaa-121">Exemple de sortie</span><span class="sxs-lookup"><span data-stu-id="2eeaa-121">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="2eeaa-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2eeaa-122">See also</span></span>

- [<span data-ttu-id="2eeaa-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2eeaa-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2eeaa-124">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2eeaa-124">Properties</span></span>](./properties.md)
- [<span data-ttu-id="2eeaa-125">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="2eeaa-125">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="2eeaa-126">Comparaison entre propriétés et indexeurs</span><span class="sxs-lookup"><span data-stu-id="2eeaa-126">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="2eeaa-127">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="2eeaa-127">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="2eeaa-128">Interfaces</span><span class="sxs-lookup"><span data-stu-id="2eeaa-128">Interfaces</span></span>](../interfaces/index.md)
