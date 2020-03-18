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
# <a name="interface-properties-c-programming-guide"></a>Propriétés d'interface (Guide de programmation C#)

Des propriétés peuvent être déclarées dans une [interface](../../language-reference/keywords/interface.md). L’exemple suivant déclare un accessoir de propriété d’interface :

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Les propriétés d’interface n’ont généralement pas de corps. Les accesseurs indiquent si la propriété est lue-écriture, lu-seulement, ou écrire-seulement. Contrairement aux classes et aux structs, déclarer les accesseurs sans corps ne déclare pas une [propriété auto-mise en œuvre.](auto-implemented-properties.md) En commençant par le C 8.0, une interface peut définir une implémentation par défaut pour les membres, y compris les propriétés. Définir une implémentation par défaut pour une propriété dans une interface est rare car les interfaces peuvent ne pas définir les champs de données d’instance.

## <a name="example"></a> Exemple

Dans cet exemple, l’interface `IEmployee` a une propriété en lecture-écriture, `Name`, et une propriété en lecture seule, `Counter`. La classe `Employee` implémente l’interface `IEmployee` et utilise ces deux propriétés. Le programme lit le nom d’un nouvel employé et le nombre actuel d’employés et affiche le nom de l’employé et le nombre d’employés calculé.

Vous pouvez utiliser le nom qualifié complet de la propriété, qui fait référence à l’interface dans laquelle le membre est déclaré. Par exemple :

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

L’exemple précédent démontre [la mise en œuvre explicite de l’interface](../interfaces/explicit-interface-implementation.md). Par exemple, si la classe `Employee` implémente deux interfaces, `ICitizen` et `IEmployee`, et que les deux interfaces ont la même propriété `Name`, l’implémentation de membre d’interface explicite est nécessaire. Autrement dit, la déclaration de propriété suivante :

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
