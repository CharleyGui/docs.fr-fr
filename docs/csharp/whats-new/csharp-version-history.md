---
title: Histoire du langage C# | Guide C#
description: À quoi ressemblait le langage dans ses versions antérieures et comment a-t-il évolué depuis ?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 9114395a5c6cfd8df5da18024921c35828947e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399685"
---
# <a name="the-history-of-c"></a>Histoire du langage C\#

Cet article fournit un historique de chaque version majeure du langage C#. L’équipe C# continue d’innover et d’ajouter de nouvelles fonctionnalités. L’état détaillé des fonctionnalités de langage, notamment celles prises en compte pour les versions à venir, est disponible dans le [dépôt dotnet/roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) sur GitHub.

> [!IMPORTANT]
> Le langage C# s’appuie sur des types et des méthodes dans ce que la spécification C# définit comme une *bibliothèque standard* pour certaines fonctionnalités. La plateforme .NET fournit ces types et ces méthodes dans des packages. Par exemple, le traitement des exceptions. Chaque instruction ou expression`throw` est vérifiée pour s’assurer de l’objet levé est dérivé de <xref:System.Exception>. De même, chaque `catch` est vérifié pour assurer que le type intercepté est dérivé de <xref:System.Exception>. Chaque version peut ajouter de nouvelles spécifications. Pour utiliser les dernières fonctionnalités de langage dans les environnements plus anciens, vous devrez peut-être installer des bibliothèques spécifiques. Ces dépendances sont décrites dans la page pour chaque version spécifique. Pour en savoir plus, consultez les [relations entre le langage et la bibliothèque](relationships-between-language-and-library.md) pour l’arrière-plan sur cette dépendance.

Les outils de build C# considèrent la dernière version majeure du langage comme la version du langage par défaut. Il peut exister des versions intermédiaires entre les versions majeures, détaillées dans d’autres articles de cette section. Pour utiliser les fonctionnalités les plus récentes dans une version mineure, vous devez [configurer la version du langage du compilateur](../language-reference/configure-language-version.md) et sélectionner la version. Il y a eu trois versions intermédiaires depuis C# 7.0 :

- [C 7.3](csharp-7-3.md):
  - C# 7.3 est disponible à compter de [Visual Studio 2017 version 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) et du [Kit SDK .NET Core 2.1](../../core/whats-new/dotnet-core-2-1.md).
- [C# 7.2](csharp-7-2.md) :
  - C 7.2 est disponible à partir de [Visual Studio 2017 version 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) et [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).
- [C 7.1](csharp-7-1.md):
  - C# 7.1 est disponible à compter de [Visual Studio 2017 version 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) et du [Kit SDK .NET Core 2.0](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C# version 1.0

Lorsque vous revenez en arrière et regardez, la version 1.0 de C, sortie avec Visual Studio .NET 2002, ressemblait beaucoup à Java. Dans ses [objectifs de conception énoncés pour ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), il cherchait à être un « langage orienté objet simple, moderne et généraliste ».  À l’époque, ressembler à Java signifiait qu’il avait atteint ces objectifs de conception.

Mais si vous repensez à C# 1.0 maintenant, cela peut vous donner le vertige. Il lui manquait des fonctionnalités asynchrones intégrées et certaines des fonctionnalités liées aux génériques qui sont aujourd’hui pour vous une évidence. En fait, il ne proposait pas du tout de génériques.  Et [LINQ](../linq/index.md) ? Pas encore disponible. Il fallait attendre encore plusieurs années.

C# version 1.0 semblait dénué de fonctionnalités, par rapport à aujourd’hui. Vous vous retrouviez à écrire plus ou moins du code détaillé. Mais il faut bien commencer quelque part. C# version 1.0 était une alternative viable à Java sur la plateforme Windows.

Les principales fonctionnalités du langage C# 1.0 étaient les suivantes :

- [Classes](../programming-guide/classes-and-structs/classes.md)
- [Structs](../language-reference/builtin-types/struct.md)
- [Interfaces](../programming-guide/interfaces/index.md)
- [Événements](../events-overview.md)
- [Propriétés](../properties.md)
- [Délégués](../delegates-overview.md)
- [Expressions](../programming-guide/statements-expressions-operators/expressions.md)
- [Déclarations](../programming-guide/statements-expressions-operators/statements.md)
- [Attributs](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# version 1.2

Version 1.2 de Cmd expédiée avec Visual Studio .NET 2003. Cette version contenait quelques améliorations mineures du langage. La principale est que, à compter de cette version, le code était généré dans une boucle `foreach` (appelée <xref:System.IDisposable.Dispose%2A>) sur un <xref:System.Collections.IEnumerator> quand ce <xref:System.Collections.IEnumerator> implémentait <xref:System.IDisposable>.

## <a name="c-version-20"></a>C# version 2.0

Les choses commencent alors à devenir intéressantes. Examinons certaines fonctionnalités majeures de C# 2.0, sorti en 2005, en même temps que Visual Studio 2005 :

- [Génériques](../programming-guide/generics/index.md)
- [Types partiels](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Méthodes anonymes](../language-reference/operators/delegate-operator.md)
- [types valeur Nullable](../language-reference/builtin-types/nullable-value-types.md)
- [Itérateurs](../programming-guide/concepts/iterators.md)
- [Covariance et contravariance](../programming-guide/concepts/covariance-contravariance/index.md)

D’autres fonctionnalités de C# 2.0 ajoutaient des capacités aux fonctionnalités existantes :

- Accessibilité distincte des accesseurs Get/Set
- Conversions de groupes de méthodes (délégués)
- Classes statiques
- Inférence de délégué

Alors que C# avait démarré en tant que langage orienté objet générique, C# version 2.0 a rapidement changé tout ça. En effet, maintenant que le langage existait, il s’agissait de s’attaquer à certains problèmes majeurs que rencontraient les développeurs. Et de s’y attaquer de manière significative.

Avec les génériques, les types et les méthodes peuvent fonctionner sur un type arbitraire tout en assurant quand même la cohérence des types. À titre d’exemple, un <xref:System.Collections.Generic.List%601> vous permet d’avoir `List<string>` ou `List<int>` et d’effectuer des opérations qui maintiennent la cohérence des types sur des chaînes ou entiers alors que vous itérez en leur sein. Il vaut mieux utiliser des génériques que créer `ListInt` qui dérive de `ArrayList` ou effectuer un cast de `Object` pour chaque opération.

C# version 2.0 a introduit les itérateurs. En bref, les itérateurs permettent d’examiner tous les éléments dans un `List` (ou d’autres types énumérables) avec une boucle `foreach`. Le fait de disposer d’itérateurs comme composants de premier ordre du langage en a considérablement amélioré la lisibilité et la capacité de raisonnement des utilisateurs vis-à-vis du code.

Pourtant, C# était toujours en train de courir derrière Java. Java avait déjà publié des versions qui incluaient des génériques et des itérateurs. Mais cela allait bientôt changer quand les deux langages poursuivraient des chemins différents.

## <a name="c-version-30"></a>C# version 3.0

C# version 3.0 est apparu fin 2007, en même temps que Visual Studio 2008, même si l’éventail complet des fonctionnalités du langage n’a réellement voir le jour qu’avec le .NET Framework version 3.5. Cette version a insufflé un changement majeur dans l’évolution de C#. Elle a imposé C# en tant que langage de programmation vraiment formidable. Examinons certaines fonctionnalités importantes dans cette version :

- [Propriétés mises en œuvre automatiques](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Types anonymes](../programming-guide/classes-and-structs/anonymous-types.md)
- [Expressions de requête](../linq/query-expression-basics.md)
- [Expressions Lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Arbres d’expression](../expression-trees.md)
- [Méthodes d’extension](../programming-guide/classes-and-structs/extension-methods.md)
- [Variables locales implicitement typées](../language-reference/keywords/var.md)
- [Méthodes partielles](../language-reference/keywords/partial-method.md)
- [Initialisateurs d’objets et de collecte](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Rétrospectivement, nombre de ces fonctionnalités semblent à la fois inéluctables et inséparables. Elles s’assemblent de façon stratégique. L’expression de requête, également appelée LINQ (Language-Integrated Query), était globalement considérée comme la fonctionnalité remarquable de cette version de C#.

Un point de vue plus nuancé s’intéresse aux arborescences d’expressions, aux expressions lambda et aux types anonymes sur lesquels se construit LINQ. Mais, dans les deux cas, C# 3.0 présentait un concept révolutionnaire. C# 3.0 jetait les bases qui allaient permettre à C# de devenir un langage fonctionnel/orienté objet hybride.

Plus précisément, il devint alors possible d’écrire des requêtes déclaratives de style SQL pour effectuer des opérations sur des collections, entre autres choses. Au lieu d’écrire une boucle `for` pour calculer la moyenne d’une liste d’entiers, vous pouviez alors simplement utiliser `list.Average()`. La combinaison des expressions de requête et des méthodes d’extension a permis à de telles listes d’entiers de paraître beaucoup plus intelligentes.

Il a fallu du temps aux utilisateurs pour comprendre et intégrer ce concept, mais ils y sont progressivement parvenus. Et aujourd’hui, bien des années plus tard, le code est beaucoup plus concis, simple et fonctionnel.

## <a name="c-version-40"></a>C# version 4.0

La version 4.0 de C, sortie avec Visual Studio 2010, aurait eu du mal à se tenir au statut révolutionnaire de la version 3.0. Avec la version 3.0, le langage C# est bel et bien sorti de l’ombre de Java pour être propulsé sur le devant de la scène. Il allait même rapidement devenir élégant.

La version suivante introduisit de nouvelles fonctionnalités intéressantes :

- [Liaison dynamique](../language-reference/builtin-types/reference-types.md)
- [Arguments nommés/facultatifs](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Covariance et contravariance génériques](../../standard/generics/covariance-and-contravariance.md)
- [Types interop incorporés](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Les types interop incorporés ont permis d’atténuer une difficulté de déploiement. La covariance et la contravariance génériques vous donnent plus de contrôle sur l’utilisation des génériques, mais elles sont un peu académiques et probablement plus appréciées des auteurs de frameworks et de bibliothèques. Les paramètres nommés et facultatifs vous permettent d’éliminer les nombreuses surcharges de méthode et s’avèrent plus pratiques. Mais aucune de ces fonctionnalités ne représente un vrai changement de paradigme.

La fonctionnalité majeure était plutôt l’introduction du mot clé `dynamic`. Le mot clé `dynamic` introduisit dans C# version 4.0 la possibilité de remplacer le compilateur lors de la saisie au moment de la compilation. En utilisant le mot clé dynamic, vous pouvez créer des constructions semblables aux langages dynamiquement typés comme JavaScript. Vous pouvez créer un `dynamic x = "a string"`, puis y ajouter six, et ainsi laisser le runtime se débrouiller avec ce qui doit se produire par la suite.

La liaison dynamique offre la possibilité de commettre des erreurs, mais également de contrôler davantage le langage.

## <a name="c-version-50"></a>C# version 5.0

La version 5.0 de C, sortie avec Visual Studio 2012, était une version ciblée de la langue. Presque tous les efforts déployés pour cette version portaient sur un autre concept révolutionnaire du langage : le modèle `async` et `await` pour la programmation asynchrone.  Voici la liste des fonctionnalités principales :

- [Membres asynchrones](../async.md)
- [Attributs d’informations de l’appelant](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a> Voir aussi

- [Projet de code : Attributs des informations de l’appelant en C# 5.0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

L’attribut d’informations de l’appelant vous permet de récupérer facilement des informations sur le contexte d’exécution sans avoir recours à une multitude de code de réflexion réutilisable. Nombre de ses usages ont trait aux diagnostics et aux tâches de journalisation.

Mais `async` et `await` sont les véritables vedettes de cette version. Quand ces fonctionnalités sont apparues en 2012, C# a encore modifié la donne en intégrant l’asynchronie en tant que participant de premier ordre dans le langage. Si vous avez déjà eu affaire à de longues opérations et à l’implémentation de rappels, vous avez probablement adoré cette fonctionnalité de langage.

## <a name="c-version-60"></a>C# version 6.0

Avec les versions 3.0 et 5.0, C# avait ajouté d’importantes nouvelles fonctionnalités à un langage orienté objet. Avec la version 6.0, sortie avec Visual Studio 2015, elle s’éloignerait de faire une fonction de tueur dominante et au lieu de sortir de nombreuses fonctionnalités plus petites qui ont rendu la programmation C plus productive. En voici quelques-unes :

- [Importations statiques](./csharp-6.md#using-static)
- [Filtres d’exceptions](./csharp-6.md#exception-filters)
- [Initialiseurs de propriétés automatiques](./csharp-6.md#auto-property-initializers)
- [Membres expression-bodied](./csharp-6.md#expression-bodied-function-members)
- [Propagateur Null](./csharp-6.md#null-conditional-operators)
- [Interpolation de chaîne](./csharp-6.md#string-interpolation)
- [opérateur nameof](./csharp-6.md#the-nameof-expression)
- [Initialiseurs d’index](csharp-6.md#extension-add-methods-in-collection-initializers)

Quelques autres nouvelles fonctions :

- Await dans des blocs catch/finally
- Valeurs par défaut pour les propriétés d’accesseur Get

Chacune de ces fonctionnalités est intéressante individuellement. Mais si vous les examinez dans leur ensemble, un modèle intéressant se dégage. Dans cette version, C# a éliminé le texte réutilisable du langage pour rendre le code plus laconique et plus lisible. Ainsi, pour les amateurs de code propre et simple, cette version du langage était une énorme victoire.

Une autre nouveauté a été proposée avec cette version, même s’il ne s’agit pas d’une fonctionnalité de langage traditionnelle à proprement dit. [Le compilateur Roslyn a été publié en tant que service](https://github.com/dotnet/roslyn). Le compilateur C# est à présent écrit en C# et vous pouvez l’utiliser dans le cadre de vos efforts de programmation.

## <a name="c-version-70"></a>C# version 7.0

La version majeure la plus récente est la version 7.0 de C, sortie avec Visual Studio 2017. Cette version propose des évolutions intéressantes dans l’esprit de C# 6.0, mais sans le compilateur en tant que service. Voici quelques-unes des nouvelles fonctionnalités :

- [Variables out](./csharp-7.md#out-variables)
- [Tuples et déconstruction](./csharp-7.md#tuples)
- [Critères spéciaux](./csharp-7.md#pattern-matching)
- [Fonctions locales](./csharp-7.md#local-functions)
- [Membres expression-bodied étendus](./csharp-7.md#more-expression-bodied-members)
- [Variables locales et retours ref](./csharp-7.md#ref-locals-and-returns)

Autres fonctionnalités disponibles :

- [Éléments ignorés](./csharp-7.md#discards)
- [Littéraux binaires et séparateurs numériques](./csharp-7.md#numeric-literal-syntax-improvements)
- [Expressions throw](./csharp-7.md#throw-expressions)

Toutes ces fonctionnalités offrent de nouvelles capacités appréciables aux développeurs ainsi que la possibilité d’écrire du code encore plus propre. Il s’agit notamment de condenser la déclaration des variables à utiliser avec le mot clé `out` et en autorisant plusieurs valeurs de retour par le biais d’un tuple.

Par ailleurs, les utilisations de C# sont de plus en plus larges. .NET Core cible à présent n’importe quel système d’exploitation et garde les yeux rivés sur le cloud et la portabilité.  Ces nouvelles fonctions occupent sans aucun doute les pensées des concepteurs du langage, en plus des fonctionnalités à venir.

_Article_ [_initialement publié sur le blog NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, avec l’aimable autorisation d’Erik Dietrich et de Patrick Smacchia._
