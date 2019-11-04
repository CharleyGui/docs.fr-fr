---
title: Passage de paramètres - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 22f58bda5aa5b60248902a4130f3ea9b6caa65cf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419126"
---
# <a name="passing-parameters-c-programming-guide"></a>Passage de paramètres (Guide de programmation C#)
En C#, les arguments peuvent être passés aux paramètres par valeur ou par référence. Avec le passage par référence, les fonctions membres, les méthodes, les propriétés, les indexeurs, les opérateurs et les constructeurs peuvent changer la valeur des paramètres et rendre cette modification persistante dans l’environnement d’appel. Pour passer un paramètre par référence avec l’intention de changer la valeur, utilisez le mot clé `ref` ou `out`. Pour passer un paramètre par référence avec l’intention d’éviter la copie, mais de ne pas changer la valeur, utilisez le modificateur `in`. Pour plus de simplicité, les exemples de cette rubrique utilisent uniquement le mot clé `ref`. Pour plus d’informations sur la différence entre `in`, `ref` et `out`, consultez [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md) et [out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 L’exemple suivant illustre la différence entre les paramètres de référence et de valeur.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
- [Passage de paramètres de type valeur](./passing-value-type-parameters.md)  
  
- [Passage de paramètres de type référence](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Liste des arguments](~/_csharplang/spec/expressions.md#argument-lists) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Méthodes](./methods.md)
