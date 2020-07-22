---
title: Comment initialiser des objets à l’aide d’un initialiseur d’objet-Guide de programmation C#
description: Découvrez comment utiliser des initialiseurs d’objets pour initialiser des objets de type en C# sans appeler un constructeur. Utilisez un initialiseur d’objet pour définir un type anonyme.
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0781b168b0ae8b8383affe19d2721da67f662045
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865032"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Comment initialiser des objets à l’aide d’un initialiseur d’objet (Guide de programmation C#)

Vous pouvez utiliser des initialiseurs d’objets pour initialiser des objets de type de façon déclarative sans appeler explicitement un constructeur pour le type.  
  
Les exemples suivants montrent comment utiliser des initialiseurs d’objets avec des objets nommés. Le compilateur traite les initialiseurs d’objets en accédant d’abord au constructeur d’instance par défaut, puis en traitant les initialisations des membres. Ainsi, si le constructeur sans paramètre est déclaré comme `private` dans la classe, les initialiseurs d’objets qui nécessitent un accès public échoueront.
  
Vous devez utiliser un initialiseur d’objet si vous définissez un type anonyme. Pour plus d’informations, consultez [Comment retourner des sous-ensembles de propriétés d’éléments dans une requête](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Exemple  

L’exemple suivant montre comment initialiser un nouveau type `StudentName` à l’aide d’initialiseurs d’objets. Cet exemple définit des propriétés dans le type `StudentName` :
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Des initialiseurs d’objet peuvent être utilisés pour définir des indexeurs dans un objet. L’exemple suivant définit une classe `BaseballTeam` qui utilise un indexeur pour obtenir et définir des joueurs à des positions différentes. L’initialiseur peut affecter des joueurs en fonction de l’abréviation de la position ou du chiffre utilisé pour désigner la position sur les feuilles de match :

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Initialiseurs d’objets et de collections](object-and-collection-initializers.md)
