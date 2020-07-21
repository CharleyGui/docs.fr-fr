---
title: Propriétés implémentées automatiquement - Guide de programmation C#
description: Pour une propriété implémentée automatiquement en C#, le compilateur crée un champ de stockage privé et anonyme accessible uniquement par le biais des accesseurs d’extraction et de définition de la propriété.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: f58f9a23f26bde7e80d834528d94e38af1231e7b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474473"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Propriétés implémentées automatiquement (Guide de programmation C#)

En C# 3.0 et versions ultérieures, les propriétés implémentées automatiquement rendent la déclaration de propriété plus concise quand aucune logique supplémentaire n’est requise dans les accesseurs de propriété. Elles permettent également au code client de créer des objets. Quand vous déclarez une propriété comme indiqué dans l'exemple suivant, le compilateur crée un champ de stockage privé et anonyme uniquement accessible via les accesseurs `get` et `set` de la propriété.
  
## <a name="example"></a>Exemple

L'exemple suivant montre une classe simple qui a des propriétés implémentées automatiquement :  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

Vous ne pouvez pas déclarer les propriétés implémentées automatiquement dans les interfaces. Les propriétés implémentées automatiquement déclarent un champ de stockage d’instance privée, et les interfaces peuvent ne pas déclarer de champs d’instance. La déclaration d’une propriété dans une interface sans définition de corps déclare une propriété avec des accesseurs qui doivent être implémentés par chaque type qui implémente cette interface.

En C# 6 et versions ultérieures, vous pouvez initialiser des propriétés implémentées automatiquement de la même façon que des champs :  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

La classe qui est illustrée dans l'exemple précédent est mutable. Le code client peut modifier les valeurs dans les objets après la création. Dans les classes complexes qui contiennent un comportement significatif (méthodes) ainsi que des données, il est souvent nécessaire d’avoir des propriétés publiques. Toutefois, pour les petites classes ou les petits structs qui encapsulent simplement un ensemble de valeurs (données) et qui ont peu de comportements ou aucun, vous devez rendre les objets immuables en déclarant l’accesseur set comme étant [privé](../../language-reference/keywords/private.md) (immuables pour les consommateurs) ou en déclarant uniquement un accesseur get (immuables partout sauf dans le constructeur).  Pour plus d’informations, consultez [comment implémenter une classe Lightweight avec des propriétés implémentées automatiquement](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).

## <a name="see-also"></a>Voir aussi

- [Propriétés](./properties.md)
- [Modificateurs](/dotnet/csharp/language-reference/keywords)
