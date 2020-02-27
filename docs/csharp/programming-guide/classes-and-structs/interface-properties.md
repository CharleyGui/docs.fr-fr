---
title: Propriétés d'interface - Guide de programmation C#
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626618"
---
# <a name="interface-properties-c-programming-guide"></a>Propriétés d'interface (Guide de programmation C#)

Des propriétés peuvent être déclarées dans une [interface](../../language-reference/keywords/interface.md). L’exemple suivant déclare un accesseur de propriété d’interface :

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Les propriétés d’interface n’ont généralement pas de corps. Les accesseurs indiquent si la propriété est en lecture-écriture, en lecture seule ou en écriture seule. Contrairement aux classes et aux structs, la déclaration des accesseurs sans corps ne déclare pas de [propriété implémentée automatiquement](auto-implemented-properties.md). À partir C# de 8,0, une interface peut définir une implémentation par défaut pour les membres, y compris les propriétés. La définition d’une implémentation par défaut pour une propriété dans une interface est rare, car les interfaces ne peuvent pas définir des champs de données d’instance.

## <a name="example"></a>Exemple

Dans cet exemple, l’interface `IEmployee` a une propriété en lecture-écriture, `Name`, et une propriété en lecture seule, `Counter`. La classe `Employee` implémente l’interface `IEmployee` et utilise ces deux propriétés. Le programme lit le nom d’un nouvel employé et le nombre actuel d’employés et affiche le nom de l’employé et le nombre d’employés calculé.

Vous pouvez utiliser le nom qualifié complet de la propriété, qui fait référence à l’interface dans laquelle le membre est déclaré. Par exemple :

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

L’exemple précédent illustre l' [implémentation d’interface explicite](../interfaces/explicit-interface-implementation.md). Par exemple, si la classe `Employee` implémente deux interfaces, `ICitizen` et `IEmployee`, et que les deux interfaces ont la même propriété `Name`, l’implémentation de membre d’interface explicite est nécessaire. Autrement dit, la déclaration de propriété suivante :

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

implémente la propriété `Name` dans l’interface `IEmployee`, alors que la déclaration suivante :

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

implémente la propriété `Name` dans l’interface `ICitizen`.

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a>Exemple de sortie

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Propriétés](./properties.md)
- [Utilisation de propriétés](./using-properties.md)
- [Comparaison entre propriétés et indexeurs](../indexers/comparison-between-properties-and-indexers.md)
- [Indexeurs](../indexers/index.md)
- [Interfaces](../interfaces/index.md)
