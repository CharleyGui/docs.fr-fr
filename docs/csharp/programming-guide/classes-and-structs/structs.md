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
# <a name="structs-c-programming-guide"></a>Structures (Guide de programmation C#)

Les structs sont définis à l’aide du mot clé [struct](../../language-reference/keywords/struct.md), par exemple :  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Les structs partagent quasiment la même syntaxe que les classes. Le nom du struct doit être un [nom d’identificateur](../inside-a-program/identifier-names.md) C# valide. Les structs sont plus limités que les classes des manières suivantes :  
  
- Au sein d’une déclaration de struct, les champs ne peuvent pas être initialisés à moins d’être déclarés comme étant de type const ou static.  
- Un struct ne peut pas déclarer de constructeur sans paramètre ni de finaliseur.  
- Les structs sont copiés lors de l'assignation. Lorsqu'un struct est assigné à une nouvelle variable, toutes les données sont copiées et les modifications apportées à la nouvelle copie ne changent pas les données de la copie d'origine. Il est important de vous en souvenir quand vous utilisez des collections de types valeur telles que `Dictionary<string, myStruct>`.  
- Les structs sont des types valeur, contrairement aux classes, qui sont des types référence.  
- Contrairement aux classes, il est possible d’instancier les structs sans avoir recours à un opérateur `new`.  
- Les structs peuvent déclarer des constructeurs qui ont des paramètres.
- Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe. Tous les structs héritent directement de <xref:System.ValueType>, qui hérite de <xref:System.Object>.  
- Un struct peut implémenter des interfaces.
- Un struct ne peut pas être `null`, et une variable de struct ne peut pas se voir assigner `null`, sauf si elle est déclarée en tant que type nullable.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](index.md)
- [Classes](classes.md)
- [Types Nullable](../nullable-types/index.md)
- [Noms d’identificateur](../inside-a-program/identifier-names.md)
- [Utilisation de structs](using-structs.md)
- [Guide pratique pour différencier le passage d’un struct et le passage d’une référence de classe à une méthode](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
