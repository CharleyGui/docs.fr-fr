---
title: Membres - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: affe2752712bfd40516861abf84bdee11528168c
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609487"
---
# <a name="members-c-programming-guide"></a>Membres (Guide de programmation C#)

Les classes et les structs ont des membres qui représentent leurs données et leur comportement. Les membres d’une classe incluent tous les membres déclarés de la classe, ainsi que tous les membres (à l’exception des constructeurs et des finaliseurs) déclarés dans toutes les classes de sa hiérarchie d’héritage. Les membres privés dans les classes de base sont hérités, mais ne sont pas accessibles à partir des classes dérivées.  
  
 Le tableau suivant liste les types de membres qu'une classe ou un struct peut contenir :  
  
|Membre|Description|  
|------------|-----------------|  
|[Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)|Les champs sont des variables déclarées au niveau de la classe. Un champ peut être un type numérique intégré ou une instance d’une autre classe. Par exemple, une classe de calendrier peut avoir un champ qui contient la date actuelle.|  
|[Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)|Les constantes sont des champs dont la valeur est définie au moment de la compilation et ne peut pas être modifiée.|  
|[Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)|Les propriétés sont des méthodes sur une classe, accessibles comme si elles étaient des champs de cette classe. Une propriété peut fournir une protection pour un champ de classe afin d’éviter qu’il ne soit modifié sans que de l’objet en ait connaissance.|  
|[Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)|Les méthodes définissent les actions qu’une classe peut effectuer. Les méthodes peuvent accepter des paramètres qui fournissent des données d’entrée et peuvent retourner des données de sortie au moyen de paramètres. Les méthodes peuvent également retourner une valeur directement, sans utiliser de paramètre.|  
|[Événements](../../../csharp/programming-guide/events/index.md)|Les événements fournissent des notifications d’occurrences, comme des clics de bouton ou l’exécution réussie d’une méthode, sur d’autres objets. Les événements sont définis et déclenchés à l’aide de délégués.|  
|[Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Les opérateurs surchargés sont considérés comme des membres de type. Quand vous surchargez un opérateur, vous le définissez sous forme de méthode statique publique dans un type. Pour plus d’informations, consultez [Surcharge d’opérateur](../../../csharp/language-reference/operators/operator-overloading.md).|  
|[Indexeurs](../../../csharp/programming-guide/indexers/index.md)|Les indexeurs permettent à un objet d'être indexé d'une manière similaire aux tableaux.|  
|[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Les constructeurs sont des méthodes qui sont appelées quand l’objet est créé. Ils sont souvent utilisés pour initialiser les données d’un objet.|  
|[Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)|Les finaliseurs sont très rarement utilisés en C#. Ce sont des méthodes appelées par le moteur d’exécution quand l’objet est sur le point d’être supprimé de la mémoire. Ils sont généralement utilisés pour vérifier que toutes les ressources qui doivent être libérées sont gérées correctement.|  
|[Types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|Les types imbriqués sont des types déclarés dans un autre type. Les types imbriqués sont souvent utilisés pour décrire les objets utilisés uniquement par les types qui les contiennent.|  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)
- [Indexeurs](../../../csharp/programming-guide/indexers/index.md)
- [Événements](../../../csharp/programming-guide/events/index.md)
- [Types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md)
- [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)
