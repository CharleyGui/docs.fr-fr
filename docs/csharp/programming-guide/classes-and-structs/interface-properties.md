---
title: Propriétés d'interface - Guide de programmation C#
description: Les propriétés peuvent être déclarées sur une interface en C#. Cet exemple déclare un accesseur de propriété d’interface.
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 920381ae804a6a968bfd667171269377f3d7e448
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864967"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="3da8e-104">Propriétés d'interface (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3da8e-104">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="3da8e-105">Des propriétés peuvent être déclarées dans une [interface](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="3da8e-105">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="3da8e-106">L’exemple suivant déclare un accesseur de propriété d’interface :</span><span class="sxs-lookup"><span data-stu-id="3da8e-106">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="3da8e-107">Les propriétés d’interface n’ont généralement pas de corps.</span><span class="sxs-lookup"><span data-stu-id="3da8e-107">Interface properties typically don't have a body.</span></span> <span data-ttu-id="3da8e-108">Les accesseurs indiquent si la propriété est en lecture-écriture, en lecture seule ou en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="3da8e-108">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="3da8e-109">Contrairement aux classes et aux structs, la déclaration des accesseurs sans corps ne déclare pas de [propriété implémentée automatiquement](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3da8e-109">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="3da8e-110">À compter de C# 8,0, une interface peut définir une implémentation par défaut pour les membres, y compris les propriétés.</span><span class="sxs-lookup"><span data-stu-id="3da8e-110">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="3da8e-111">La définition d’une implémentation par défaut pour une propriété dans une interface est rare, car les interfaces ne peuvent pas définir des champs de données d’instance.</span><span class="sxs-lookup"><span data-stu-id="3da8e-111">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="3da8e-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3da8e-112">Example</span></span>

<span data-ttu-id="3da8e-113">Dans cet exemple, l’interface `IEmployee` a une propriété en lecture-écriture, `Name`, et une propriété en lecture seule, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="3da8e-113">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="3da8e-114">La classe `Employee` implémente l’interface `IEmployee` et utilise ces deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="3da8e-114">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="3da8e-115">Le programme lit le nom d’un nouvel employé et le nombre actuel d’employés et affiche le nom de l’employé et le nombre d’employés calculé.</span><span class="sxs-lookup"><span data-stu-id="3da8e-115">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="3da8e-116">Vous pouvez utiliser le nom qualifié complet de la propriété, qui fait référence à l’interface dans laquelle le membre est déclaré.</span><span class="sxs-lookup"><span data-stu-id="3da8e-116">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="3da8e-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3da8e-117">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="3da8e-118">L’exemple précédent illustre l' [implémentation d’interface explicite](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="3da8e-118">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="3da8e-119">Par exemple, si la classe `Employee` implémente deux interfaces, `ICitizen` et `IEmployee`, et que les deux interfaces ont la même propriété `Name`, l’implémentation de membre d’interface explicite est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3da8e-119">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="3da8e-120">Autrement dit, la déclaration de propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="3da8e-120">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="3da8e-121">implémente la propriété `Name` dans l’interface `IEmployee`, alors que la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="3da8e-121">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="3da8e-122">implémente la propriété `Name` dans l’interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="3da8e-122">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="3da8e-123">Exemple de sortie</span><span class="sxs-lookup"><span data-stu-id="3da8e-123">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="3da8e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3da8e-124">See also</span></span>

- [<span data-ttu-id="3da8e-125">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3da8e-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3da8e-126">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3da8e-126">Properties</span></span>](./properties.md)
- [<span data-ttu-id="3da8e-127">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="3da8e-127">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="3da8e-128">Comparaison entre propriétés et indexeurs</span><span class="sxs-lookup"><span data-stu-id="3da8e-128">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="3da8e-129">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="3da8e-129">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="3da8e-130">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3da8e-130">Interfaces</span></span>](../interfaces/index.md)
