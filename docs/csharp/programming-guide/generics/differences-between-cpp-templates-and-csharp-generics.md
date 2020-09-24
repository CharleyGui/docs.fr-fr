---
title: Différences entre les modèles C++ et les génériques C# - Guide de programmation C#
description: En savoir plus sur les différences entre les modèles C++ et les génériques C#. Les deux sont des fonctionnalités de langage qui fournissent la prise en charge des types paramétrables.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 58b424e4dacd8b691c353f4eda1950f9710ef081
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167364"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Différences entre les modèles C++ et les génériques C# (Guide de programmation C#)

Les génériques C# et les modèles C++ sont des fonctionnalités linguistiques qui prennent en charge les types paramétrables. Toutefois, il existe de nombreuses différences entre les deux. Au niveau de la syntaxe, les génériques C# constituent une approche plus simple des types paramétrables, sans la complexité des modèles C++. De plus, C# n’essaie pas de fournir toutes les fonctionnalités fournies par les modèles C++. Au niveau de l’implémentation, la principale différence est que les substitutions de type générique C# sont effectuées au moment de l’exécution. Ainsi, les informations de type générique sont conservées pour les objets instanciés. Pour plus d’informations, consultez [Génériques dans le runtime](./generics-in-the-run-time.md).  
  
 Voici les principales différences entre les modèles C++ et les génériques C# :  
  
- Les génériques C# n’offrent pas le même niveau de flexibilité que les modèles C++. Par exemple, il n’est pas possible d’appeler des opérateurs arithmétiques dans une classe générique C#, bien qu’il soit possible d’appeler des opérateurs définis par l’utilisateur.  
  
- C# n’autorise pas les paramètres de modèle sans type, tels que `template C<int i> {}`.  
  
- C# ne prend pas en charge la spécialisation explicite (une implémentation personnalisée d’un modèle pour un type spécifique).  
  
- C# ne prend pas en charge la spécialisation partielle (une implémentation personnalisée pour un sous-ensemble des arguments de type).  
  
- C# n’autorise pas l’utilisation du paramètre de type comme classe de base pour le type générique.  
  
- C# n’autorise pas les paramètres de type à avoir des types par défaut.  
  
- En C#, un paramètre de type générique ne peut pas être lui-même un générique, bien que les types construits puissent être utilisés comme des génériques. C++ autorise les paramètres de modèle.  
  
- C++ autorise le code qui peut ne pas être valide pour tous les paramètres de type dans le modèle, qui est ensuite vérifié pour identifier le type spécifique utilisé comme paramètre de type. C# exige que le code dans une classe soit écrit de telle sorte qu’il fonctionne avec tout type qui satisfait aux contraintes. Par exemple, en C++ il est possible d’écrire une fonction qui utilise les opérateurs arithmétiques `+` et `-` sur des objets du paramètre de type, ce qui générera une erreur au moment de l’instanciation du modèle avec un type qui ne prend pas en charge ces opérateurs. Ceci n’est pas autorisé par C#. Les seules constructions de langage autorisées sont celles qui peuvent être déduites des contraintes.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Introduction aux génériques](./index.md)
- [Modèles](/cpp/cpp/templates-cpp)
