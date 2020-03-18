---
title: Présentation de .NET
description: Visite guidée de certaines fonctionnalités principales de .NET.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: 61d4792b1f1b92dd59442ee38810da96c6cf63bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241141"
---
# <a name="tour-of-net"></a>Présentation de .NET

.NET est une plateforme de développement généraliste. Elle comporte plusieurs fonctionnalités clés, telles que la prise en charge de plusieurs langages de programmation, des modèles de programmation asynchrone et simultanée et une interopérabilité native, qui permettent un large éventail de scénarios sur plusieurs plateformes.

Cet article propose une visite guidée de certaines fonctionnalités principales de .NET. Consultez la rubrique [Composants architecturaux de .NET](components.md) pour en savoir plus sur les parties architecturales de .NET et sur leur finalité.

## <a name="how-to-run-the-code-samples"></a>Guide pratique pour exécuter les exemples de code

Pour savoir comment configurer un environnement de développement pour exécuter les exemples de code, consultez la rubrique [Bien démarrer](get-started.md). Copiez et collez les exemples de code à partir de cette page dans votre environnement pour les exécuter.

## <a name="programming-languages"></a>Langages de programmation

.NET prend en charge plusieurs langages de programmation. Les implémentations de .NET implémentent le [Common Language Infrastructure (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/), qui, entre autres, spécifie un runtime indépendant du langage et une interopérabilité des langages. Cela signifie que vous choisissez n’importe quel langage .NET pour générer des applications et services sur .NET.

Microsoft développe et prend en charge activement trois langues .NET : C, F et Visual Basic.

* C# est simple, puissant, de type sécurisé et orienté objet, tout en conservant l’expressivité et l’élégance des langages de style C. Les utilisateurs familiarisés avec le langage C et les langages similaires ont peu de difficultés à s’adapter à C#. Consultez le [Guide C#](../csharp/index.yml) pour en savoir plus sur C#.

* F# est un langage de programmation multiplateforme et fonctionnel qui prend également en charge la programmation orientée objet et impérative traditionnelle. Consultez le [Guide F#](../fsharp/index.yml) pour en savoir plus sur F#.

* Visual Basic est un langage facile à apprendre que vous utilisez pour créer une variété d’applications qui s’exécutent sur .NET. Parmi les langues .NET, la syntaxe de Visual Basic est la plus proche du langage humain ordinaire, ce qui rend souvent plus facile pour les personnes nouvelles au développement de logiciels.

## <a name="automatic-memory-management"></a>Gestion automatique de la mémoire

.NET utilise le [garbage collection (GC)](garbage-collection/index.md) pour fournir une gestion automatique de la mémoire pour les programmes. Le récupérateur de mémoire opère avec une approche différée de la gestion de la mémoire, préférant le débit de l’application à la collecte immédiate de la mémoire. Pour plus d’informations sur le garbage collector .NET, consultez [Notions de base du garbage collection (GC)](garbage-collection/fundamentals.md).

Les deux lignes suivantes allouent de la mémoire :

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Il n’existe aucun mot clé analogue pour libérer de la mémoire, car la libération de mémoire se produit automatiquement quand le récupérateur de mémoire réclame la mémoire dans son exécution planifiée.

Le garbage collector est un des services qui garantissent la *sûreté de la mémoire*. Un programme est sûr du point de vue de la mémoire s’il accède uniquement à la mémoire allouée. Par exemple, le runtime garantit qu’une application n’accède pas à la mémoire non allouée au-delà des limites d’un tableau.

Dans l’exemple suivant, le runtime lève une exception <xref:System.IndexOutOfRangeException> pour appliquer la sûreté de la mémoire :

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Utilisation des ressources non managées

Certains objets font référence à des *ressources non managées*. Les ressources non managées sont des ressources qui ne sont pas automatiquement gérées par le runtime .NET. Par exemple, un handle de fichier est une ressource non managée. Un objet <xref:System.IO.FileStream> est un objet managé, mais il fait référence à un handle de fichier qui ne l’est pas. Quand vous avez fini d’utiliser l’objet <xref:System.IO.FileStream>, vous devez libérer le handle de fichier.

Dans .NET, les objets qui font référence à des ressources non managées implémentent l’interface <xref:System.IDisposable>. Quand vous avez fini d’utiliser l’objet, vous appelez la méthode <xref:System.IDisposable.Dispose> de l’objet qui est chargée de libérer les ressources non managées. .Les langues NET fournissent une [ `using` déclaration](../csharp/language-reference/keywords/using.md) pratique pour ces objets, comme le montre l’exemple suivant :

[!code-csharp[UnmanagedResources](../../samples/snippets/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Une fois que le bloc `using` est fini, le runtime .NET appelle automatiquement la méthode <xref:System.IDisposable.Dispose> de l’objet `stream` qui libère le handle de fichier. Le runtime agit également ainsi quand une exception entraîne le contrôle à laisser le bloc.

Pour plus de détails, consultez les rubriques suivantes :

* Pour C#, consultez la rubrique [using, instruction (référence C#)](../csharp/language-reference/keywords/using-statement.md).
* Pour F#, consultez [Gestion des ressources : mot clé use](../fsharp/language-reference/resource-management-the-use-keyword.md).
* Pour Visual Basic, voir le sujet [Using Statement (Visual Basic).](../visual-basic/language-reference/statements/using-statement.md)

## <a name="type-safety"></a>Cohérence des types

Un objet est une instance d’un type spécifique. Les seules opérations autorisées pour un objet donné sont celles de son type. Un type `Dog` peut avoir des méthodes `Jump` et `WagTail`, mais pas une méthode `SumTotal`. Un programme appelle uniquement les méthodes appartenant à un type donné. Tous les autres appels entraînent une erreur au moment de la compilation ou une exception au moment de l’exécution (en cas d’utilisation de fonctionnalités dynamiques ou du type `object`).

Les langages .NET sont orientés objet avec des hiérarchies de classes de base et dérivées. Le runtime .NET autorise uniquement les casts et les appels d’objet qui s’alignent sur la hiérarchie d’objets. N’oubliez pas que chaque type défini dans un langage .NET dérive du type <xref:System.Object> de base.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

La cohérence des types est également utilisée pour aider à appliquer l’encapsulation en garantissant la fidélité des mots clés d’accesseur. Les mots clés d’accesseur sont des artefacts qui contrôlent l’accès aux membres d’un type donné par un autre code. Ils servent généralement à différentes sortes de données dans un type utilisées pour gérer son comportement.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic et F# prennent en charge l’*inférence de type* locale. L’inférence de type signifie que le compilateur déduit le type de l’expression à gauche à partir de l’expression à droite. Cela ne signifie pas que la cohérence des types est interrompue ou évitée. Le type résultant a un type fort avec tout ce que cela implique. À partir de l’exemple précédent, `dog` est réécrit pour présenter l’inférence de type, et le reste de l’exemple reste inchangé :

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F a encore plus de capacités d’inférence de type que l’inférence de type type type méthode-locale trouvée dans C et Visual Basic. Pour plus d’informations, consultez [Type Inference](../fsharp/language-reference/type-inference.md) (Inférence de type).

## <a name="delegates-and-lambdas"></a>Délégués et expressions lambda

Un délégué est représenté par une signature de méthode. Toute méthode avec cette signature peut être assignée au délégué et est exécutée quand celui-ci est appelé.

Les délégués sont semblables aux pointeurs de fonction C++, à la différence qu’ils sont de type sécurisé. Ils représentent une sorte de méthode déconnectée au sein du système de type CLR. Les méthodes classiques sont attachées à une classe et peuvent être appelées directement uniquement par des conventions d’appel statiques ou d’instance.

Dans .NET, les délégués sont souvent utilisés dans les gestionnaires d’événements, dans la définition des opérations asynchrones et dans les expressions lambda, qui sont la pierre angulaire de LINQ. Pour en savoir plus, consultez la rubrique [Délégués et expressions lambda](delegates-lambdas.md).

## <a name="generics"></a>Génériques

Les génériques permettent au programmeur d’introduire un *paramètre de type* quand il désigne leurs classes qui permet au code client (les utilisateurs du type) de spécifier le type exact à utiliser à la place du paramètre de type.

Les génériques ont été ajoutés pour aider les programmeurs à implémenter des structures de données génériques. Avant leur arrivée, pour qu’un `List` type tel que le type soit générique, `object`il faudrait travailler avec des éléments de type . Cela a eu diverses performances et problèmes sémantiques, ainsi que d’éventuelles erreurs subtiles de temps de course. Une erreur de temps de ruissellement commune est lorsqu’une structure de données contient, par exemple, des intégraux et des cordes, et qu’une <xref:System.InvalidCastException> erreur est lancée pendant le traitement des membres de la liste.

L’exemple suivant montre une exécution de programme de base utilisant une instance des types <xref:System.Collections.Generic.List%601> :

[!code-csharp[GenericsShort](../../samples/snippets/csharp/snippets/tour/GenericsShort.csx)]

Pour plus d’informations, consultez la rubrique [Vue d’ensemble des types génériques (Génériques)](generics.md).

## <a name="async-programming"></a>Programmation asynchrone

La programmation asynchrone est un concept de première classe dans .NET avec prise en charge asynchrone dans le runtime, des bibliothèques de framework et des constructions de langage .NET. En interne, ils sont basés sur des objets (comme `Task`), qui tirent parti du système d’exploitation pour effectuer aussi efficacement que possible des tâches utilisant des E/S.

Pour en savoir plus sur la programmation asynchrone dans .NET, commencez par la rubrique [Vue d’ensemble d’Async](async.md).

## <a name="language-integrated-query-linq"></a>LINQ (Language-Integrated Query)

LINQ est un ensemble puissant de fonctionnalités pour C et Visual Basic qui vous permet d’écrire un code simple et déclaratif pour l’exploitation de données. Les données peuvent se présenter sous plusieurs formes (comme des objets en mémoire, une base de données SQL ou un document XML), mais le code LINQ que vous écrivez ne diffère généralement pas d’une source de données à l’autre.

Pour en savoir plus et obtenir des exemples, consultez la rubrique [LINQ (Language Integrated Query)](using-linq.md).

## <a name="native-interoperability"></a>Interopérabilité native

Chaque système d’exploitation inclut une interface de programmation d’application (API) qui fournit des services système. .NET offre plusieurs moyens d’appeler ces API.

Le principal moyen d’effectuer une interopérabilité native est via l’« appel de code non managé » ou P/Invoke, en forme abrégée, fonctionnalité prise en charge sur les plateformes Linux et Windows. Un moyen de faire une interopérabilité native sur Windows uniquement est connu sous le nom de « COM Interop », utilisé pour travailler avec des [composants COM](/cpp/atl/introduction-to-com) dans du code managé. Il est basé sur l’infrastructure de P/Invoke, mais fonctionne légèrement différemment.

Une grande partie de la prise en charge d’interopérabilité dans Mono (et donc dans Xamarin) pour Java et Objective-C est générée de la même façon, autrement dit, ils utilisent les mêmes principes.

Pour plus d’informations sur l’interopérabilité native, consultez l’article [Interopérabilité native](native-interop/index.md).

## <a name="unsafe-code"></a>Code unsafe

En fonction de la prise en charge du langage, le CLR vous permet d’accéder à la mémoire native et d’effectuer une opération arithmétique de pointeur par le biais de code `unsafe`. Ces opérations sont nécessaires pour certains algorithmes et pour l’interopérabilité du système. L’utilisation de code unsafe, bien que puissante, est déconseillée, sauf si elle est nécessaire pour assurer l’interopérabilité avec les API système ou implémenter l’algorithme le plus efficace. Le code unsafe peut ne pas s’exécuter de la même façon dans différents environnements et perd les avantages d’un récupérateur de mémoire et de la cohérence des types. Nous vous recommandons de restreindre et centraliser le code unsafe autant que possible et de tester ce code de manière approfondie.

L’exemple suivant est une version modifiée de la méthode `ToString()` à partir de la classe `StringBuilder`. Il illustre comment l’utilisation de code `unsafe` peut implémenter efficacement un algorithme en déplaçant directement des segments de mémoire :

[!code-csharp[Unsafe](../../samples/snippets/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Étapes suivantes

Si vous êtes intéressé par une présentation des fonctionnalités de C#, consultez [Tour of C#](../csharp/tour-of-csharp/index.md) (Présentation de C#).

Si vous êtes intéressé par une présentation des fonctionnalités de F#, consultez [Visite guidée de F#](../fsharp/tour.md).

Si vous voulez vous familiariser avec l’écriture de votre propre code, visitez la page [Bien démarrer](get-started.md).

Pour obtenir des informations sur les composants importants de .NET, consultez [Composants architecturaux de .NET](components.md).
