---
title: Comment déterminer si un objet .NET Standard est sérialisable
description: Montre comment déterminer si un type de .NET Standard peut être sérialisé au moment de l’exécution.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: 9f7ab8a824b9687f68382a5edc342536289c5d09
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282327"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Comment déterminer si un objet .NET Standard est sérialisable

.NET Standard est une spécification qui définit les types et les membres qui doivent être présents sur des implémentations .NET spécifiques qui se conforment à cette version de la norme. Toutefois, .NET Standard ne définit pas si un type est sérialisable. Les types définis dans la bibliothèque de .NET Standard ne sont pas marqués avec l' <xref:System.SerializableAttribute> attribut. Au lieu de cela, des implémentations .NET spécifiques, telles que .NET Framework et .NET Core, sont libres de déterminer si un type particulier est sérialisable.

Si vous avez développé une bibliothèque qui cible .NET Standard, votre bibliothèque peut être consommée par n’importe quelle implémentation .NET qui prend en charge .NET Standard. Cela signifie que vous ne pouvez pas savoir à l’avance si un type particulier est sérialisable ; vous pouvez uniquement déterminer si elle est sérialisable au moment de l’exécution.

Vous pouvez déterminer si un objet est sérialisable au moment de l’exécution en extrayant la valeur de la <xref:System.Type.IsSerializable> propriété d’un <xref:System.Type> objet qui représente le type de cet objet. L’exemple suivant fournit une implémentation. Il définit une `IsSerializable(Object)` méthode d’extension qui indique si une <xref:System.Object> instance de peut être sérialisée.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Vous pouvez ensuite passer n’importe quel objet à la méthode pour déterminer s’il peut être sérialisé et désérialisé sur l’implémentation .NET actuelle, comme le montre l’exemple suivant :

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Sérialisation binaire](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
