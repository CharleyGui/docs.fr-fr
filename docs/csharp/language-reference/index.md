---
description: Informations de référence sur C#
title: Informations de référence sur C#
ms.date: 02/14/2017
f1_keywords:
- _CSharpKeyword
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 317f375c46eee3bb9c719afb68993cd4720e54fe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127189"
---
# <a name="c-reference"></a>Informations de référence sur C#

Cette section fournit des ressources de référence sur les mots clés, les opérateurs, les caractères spéciaux, les directives de préprocesseur, les options du compilateur, et les erreurs et avertissements du compilateur du langage C#.  
  
## <a name="in-this-section"></a>Contenu de cette section

 [Mots clés C#](./keywords/index.md)  
 Fournit des liens vers des informations sur la syntaxe et les mots clés C#.  
  
 [Opérateurs C#](./operators/index.md)  
 Fournit des liens vers des informations sur la syntaxe et les opérateurs C#.  

 [Caractères spéciaux C#](./tokens/index.md)  
 Fournit des liens vers des informations sur des caractères spéciaux contextuels en C# et leur utilisation.  

 [Directives de préprocesseur C#](./preprocessor-directives/index.md)  
 Fournit des liens vers des informations sur les commandes de compilateur permettant d’incorporer du code source en C#.  
  
 [Options du compilateur C#](./compiler-options/index.md)  
 Inclut des informations sur les options du compilateur et comment les utiliser.  
  
 [Erreurs du compilateur C#](./compiler-messages/index.md)  
 Inclut des extraits de code qui montrent la cause et la correction des erreurs du compilateur et des avertissements C#.  
  
 [Spécification du langage C#](../../../_csharplang/spec/introduction.md)  
 Spécification du langage C# 6.0. Il s’agit d’une ébauche de proposition pour le langage C# 6.0. Ce document sera affiné par le biais du Comité des normes ECMA C#. La version 5.0 a été publiée en décembre 2017 dans le document [Standard ECMA-334 5th Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf).

Les fonctionnalités ayant été implémentées dans les versions C# ultérieures à 6.0 sont représentées dans des propositions de spécification du langage. Ces documents décrivent les delta de la spécification du langage afin d’ajouter ces nouvelles fonctionnalités. Il s’agit d’un formulaire de proposition. Ces spécifications seront affinées et soumises au Comité des normes ECMA pour une révision et une incorporation formelles dans une future version de la norme C#.

 [Propositions de spécification C# 7,0](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 De nouvelles fonctionnalités ont été implémentées dans C# 7.0 : critères spéciaux, fonctions locales, déclarations de variables out, expressions throw, littéraux binaires et séparateurs numériques notamment. Ce dossier contient les spécifications de chacune de ces fonctionnalités.
  
 [Propositions de spécification C# 7,1](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 De nouvelles fonctionnalités ont été ajoutées à C# 7.1. D’abord, vous pouvez écrire une méthode `Main` qui renvoie `Task` ou `Task<int>`. Ceci vous permet d’ajouter le modificateur `async` à `Main`. L’expression `default` peut être utilisée sans type dans des emplacements où le type peut être déduit. De plus, les noms de membres de tuple peuvent être déduits. Enfin, les critères spéciaux peuvent être utilisés avec des génériques.

 [Propositions de spécification C# 7,2](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C# 7.2 apporte un certain nombre de petites fonctionnalités. Vous pouvez envoyer des arguments par référence en lecture seule à l’aide du mot clé `in`. Il existe un certain nombre de modifications de bas niveau pour soutenir la sécurité au moment de la compilation pour `Span` et d’autres types associés. Vous pouvez utiliser les arguments nommés où des arguments ultérieurs seront positionnels dans certains cas. Le modificateur d'accès `private protected` vous permet de spécifier que les appelants sont limités à des types dérivés implémentés dans le même assembly. L’opérateur `?:` peut se servir d’une référence pour une variable. Vous pouvez aussi formater des nombres binaires et hexadécimaux à l’aide d’un séparateur numérique de début.

 [Propositions de spécification C# 7,3](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C#7.3 est une nouvelle version qui comprend plusieurs petites mises à jour. Vous pouvez utiliser de nouvelles contraintes sur les paramètres de type générique. D’autres modifications facilitent l’utilisation des `fixed` champs, y compris l’utilisation des [`stackalloc`](./operators/stackalloc.md) allocations. Les variables locales déclarées avec le `ref` mot clé peuvent être réassignées pour faire référence au nouveau stockage. Vous pouvez placer des attributs sur les propriétés implémentées automatiquement qui ciblent le champ de stockage généré par le compilateur. Les variables d’expression peuvent être utilisées dans les initialiseurs. Les tuples peuvent être comparés pour savoir s’ils sont égaux (ou inégaux). Il y a également eu des améliorations pour la résolution de surcharge.
  
 [Propositions de spécification C# 8,0](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C# 8,0 est disponible avec .NET Core 3,0. Les fonctionnalités incluent les types de référence Nullable, les critères spéciaux récursifs, les méthodes d’interface par défaut, les flux asynchrones, les plages et les index, les modèles basés sur et les déclarations, l’affectation de fusion Null et les membres d’instance en lecture seule.
  
## <a name="related-sections"></a>Sections connexes  

 [Utilisation de l’environnement de développement Visual Studio pour C#](/visualstudio/get-started/csharp)  
 Fournit des liens vers des des rubriques de concepts et de tâches qui décrivent l’IDE et l’éditeur.  
  
 [Guide de programmation C#](../programming-guide/index.md)  
 Inclut des informations sur l’utilisation du langage de programmation C#.
