---
title: Indexeurs - Guide de programmation C#
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 539b2861e975c0c758c43c8a5d4cca86e3d2bb2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167537"
---
# <a name="indexers-c-programming-guide"></a>Indexeurs (Guide de programmation C#)

Les indexeurs permettent aux instances d'une classe ou d'un struct d'être indexés comme des tableaux. La valeur indexée peut être définie ou récupérée sans spécifier explicitement un membre de type ou d’instance. Les indexeurs s’apparentent aux [propriétés](../classes-and-structs/properties.md) à l’exception près que leurs accesseurs acceptent des paramètres.  

 L’exemple suivant définit une classe générique avec des méthodes d’accesseur [get](../../language-reference/keywords/get.md) et [set](../../language-reference/keywords/set.md) simples pour attribuer et récupérer des valeurs. La classe `Program` classe crée une instance de cette classe pour le stockage des chaînes.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> Pour plus d’exemples, consultez [Rubriques connexes](./index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Définitions de corps d'expression  

Il est courant pour l’accesseur get ou set d’un indexeur d’être constitué d’une instruction unique qui retourne ou définit une valeur. Les membres expression-bodied fournissent une syntaxe simplifiée pour prendre en charge ce scénario. À partir de C# 6, un indexeur en lecture seule peut être implémenté comme un membre expression-bodied, comme le montre l’exemple suivant.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Notez que `=>` introduit le corps de l’expression et que le mot clé `get` n’est pas utilisé.

À partir de C# 7.0, l’accesseur get et l’accesseur set peuvent être implémentés en tant que membres expression-bodied. Dans ce cas, les deux mots clés `get` et `set` doivent être utilisés. Par exemple :

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Vue d'ensemble des indexeurs  
  
- Les indexeurs permettent aux objets d'être indexés d'une manière similaire aux tableaux.  
  
- Un accesseur `get` retourne une valeur. Un accesseur `set` affecte une valeur.  
  
- Le mot clé [this](../../language-reference/keywords/this.md) est utilisé pour définir l’indexeur.  
  
- Le mot clé [value](../../language-reference/keywords/value.md) est utilisé pour définir la valeur affectée par l’indexeur `set`.  
  
- Les indexeurs n'ont pas besoin d'être indexés par une valeur entière. Il vous appartient de choisir comment définir le mécanisme de recherche spécifique.  
  
- Les indexeurs peuvent être surchargés.  
  
- Les indexeurs peuvent avoir plusieurs paramètres formels, par exemple, quand vous accédez à un tableau à deux dimensions.  
  
## <a name="BKMK_RelatedSections"></a>Sections connexes  
  
- [Utilisation des indexeurs](./using-indexers.md)  
  
- [Indexeurs dans les interfaces](./indexers-in-interfaces.md)  
  
- [Comparaison entre propriétés et indexeurs](./comparison-between-properties-and-indexers.md)  
  
- [Restriction d’accessibilité de l’accesseur](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Indexeurs](~/_csharplang/spec/classes.md#indexers) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Propriétés](../classes-and-structs/properties.md)
