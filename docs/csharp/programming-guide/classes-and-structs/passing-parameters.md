---
title: Passage de paramètres - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705468"
---
# <a name="passing-parameters-c-programming-guide"></a>Passage de paramètres (Guide de programmation C#)
En C#, les arguments peuvent être passés aux paramètres par valeur ou par référence. Avec le passage par référence, les fonctions membres, les méthodes, les propriétés, les indexeurs, les opérateurs et les constructeurs peuvent changer la valeur des paramètres et rendre cette modification persistante dans l’environnement d’appel. Pour passer un paramètre par référence avec l’intention de changer la valeur, utilisez le mot clé `ref` ou `out`. Pour passer un paramètre par référence avec l’intention d’éviter la copie, mais de ne pas changer la valeur, utilisez le modificateur `in`. Pour plus de simplicité, les exemples de cette rubrique utilisent uniquement le mot clé `ref`. Pour plus d’informations sur la différence entre `in`, `ref` et `out`, consultez [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md) et [out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 L’exemple suivant illustre la différence entre les paramètres de référence et de valeur.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Pour plus d'informations, voir les rubriques suivantes :  
  
- [Passage de paramètres de type valeur](./passing-value-type-parameters.md)  
  
- [Passage de paramètres de type référence](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Liste des arguments](~/_csharplang/spec/expressions.md#argument-lists) dans la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Méthodes](./methods.md)
