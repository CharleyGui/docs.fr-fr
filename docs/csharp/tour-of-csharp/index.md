---
title: Visite guidée du langage C# - Guide du langage C#
description: Novice en C# ? Découvrez les principes de base du langage.
ms.date: 04/05/2019
ms.openlocfilehash: b510342f957a259a6c7763441778461b3dd4ef1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673288"
---
# <a name="a-tour-of-the-c-language"></a>Visite guidée du C# langage

C# (prononcé « C Sharp ») est un langage de programmation simple, moderne, orienté objet et de type sécurisé. C# prend sa source dans la famille de langages C et sera immédiatement reconnaissable aux programmeurs en C, C++, Java et JavaScript.

Cette visite guidée fournit une vue d’ensemble des principaux composants du langage C# dans 7 et versions ultérieures. Si vous souhaitez explorer le langage par le biais d’exemples interactifs, consultez la [présentation C# ](../tutorials/intro-to-csharp/index.md) des didacticiels.

C# est un langage orienté objet, mais C# inclut de plus la prise en charge de la programmation ***orientée composant***. La conception logicielle moderne s’appuie de plus en plus sur les composants logiciels sous la forme de packages de fonctionnalités autonomes et autodescriptifs. Point important, ces composants présentent un modèle de programmation avec propriétés, méthodes et événements ; ils ont des attributs qui fournissent des informations déclaratives sur le composant ; et ils intègrent leur propre documentation. C# fournit des constructions de langage qui prennent directement en charge ces concepts, ce qui fait de C# un langage très naturel pour créer et utiliser des composants logiciels.

Plusieurs fonctionnalités de C# participent à la construction d’applications robustes et fiables : le ***garbage collection*** récupère automatiquement la mémoire occupée par les objets inutilisés et inaccessibles ; la ***gestion des exceptions*** fournit une approche structurée et extensible de la détection d’erreurs et la récupération ; et, grâce à la conception ***de type sécurisé*** du langage, il est impossible de lire des variables non initialisées, d’indexer des tableaux au-delà de leurs limites et d’effectuer des transtypages non contrôlés.

C# a un ***système de type unifié***. Tous les types C#, y compris les types primitifs tels que `int` et `double`, héritent d’un seul type `object` racine. Par conséquent, tous les types partagent un ensemble d’opérations communes, et des valeurs de tous types peuvent être stockées, transmises et exploitées de manière cohérente. En outre, C# prend en charge les types référence et les types valeur définis par l’utilisateur, ce qui permet l’allocation dynamique d’objets, ainsi que le stockage en ligne de structures légères.

Pour vous assurer C# que les programmes et les bibliothèques peuvent évoluer au fil du temps d’une manière compatible, l’accent est mis C#sur le contrôle de ***version*** dans la conception de. De nombreux langages de programmation n’accordent que peu d’attention à ce problème ; par conséquent, les programmes écrits dans ces langages s’arrêtent plus souvent que nécessaire lors de l’introduction de versions plus récentes des bibliothèques dépendantes. Les aspects C#de la conception de qui ont été directement influencés par les considérations relatives à la gestion des versions incluent les modificateurs de `virtual` et d' `override` distincts, les règles de résolution de surcharge de méthode et la prise en charge des déclarations de membres d’interface explicites.

## <a name="hello-world"></a>Hello World

Le programme « Hello, World » est souvent utilisé pour présenter un langage de programmation. Le voici en C# :

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

Les fichiers sources C# ont généralement l’extension de fichier `.cs`. En supposant que le programme « Hello, World » est stocké dans le fichier *Hello.cs*, le programme peut être compilé à l’aide de la ligne de commande :

```console
csc hello.cs
```

qui produit un assembly exécutable nommé *Hello. exe*. Voici la sortie produite par cette application lorsqu’elle est exécutée :

```console
Hello, World
```

> [!IMPORTANT]
> La commande `csc` effectue la compilation pour la totalité de l’infrastructure ; elle n’est pas nécessairement disponible sur toutes les plateformes.

Le programme « Hello, World » commence par une directive `using` qui fait référence à l’espace de noms `System`. Les espaces de noms représentent un moyen hiérarchique d’organiser les bibliothèques et les programmes C#. Les espaces de noms contiennent des types et d’autres espaces de noms ; par exemple, l’espace de noms `System` contient plusieurs types, notamment la classe `Console` référencée dans le programme, et d’autres espaces de noms, tels que `IO` et `Collections`. Une directive `using` qui fait référence à un espace de noms donné permet l’utilisation non qualifiée des types membres de cet espace de noms. En raison de la directive `using`, le programme peut utiliser `Console.WriteLine` comme raccourci pour `System.Console.WriteLine`.

La classe `Hello` déclarée par le programme « Hello, World » a un membre unique, la méthode nommée `Main`. La méthode `Main` est déclarée avec le modificateur statique. Si les méthodes d’instance peuvent faire référence à une instance d’objet englobante particulière avec le mot clé `this`, les méthodes statiques fonctionnent sans référence à un objet particulier. Par convention, une méthode statique nommée `Main` sert de point d’entrée d’un programme.

La sortie du programme est générée par la méthode `WriteLine` de la classe `Console` dans l’espace de noms `System`. Cette classe est fournie par les bibliothèques de classes standard, qui, par défaut, sont référencées automatiquement par le compilateur.

## <a name="elements-of-the-c-language"></a>Éléments du C# langage

Il y a beaucoup d’autres choses à apprendre sur C#. Les rubriques suivantes fournissent une vue d’ensemble des éléments du langage C#. Ces vues d’ensemble fournissent des informations de base sur tous les éléments de la langue et vous donnent les informations nécessaires pour approfondir les tâches :

- [Structure du programme](program-structure.md)
  - Découvrez les concepts clés d’organisation du langage C# : ***programmes***, ***espaces de noms***, ***types***, ***membres*** et ***assemblys***.
- [Types et variables](types-and-variables.md)
  - Découvrez les ***types valeur***, les ***types référence*** et les ***variables*** en langage C#.
- [Expressions](expressions.md)
  - Les ***expressions*** sont construites à partir de ***d’opérandes*** et ***d’opérateurs***. Les expressions produisent une valeur.
- [Instructions](statements.md)
  - On utilise des ***instructions*** pour exprimer les actions d’un programme.
- [Classes et objets](classes-and-objects.md)
  - Les ***classes*** représentent le type le plus fondamental de C#. Les ***objets*** sont des instances d’une classe. Les classes sont générées à l’aide de ***membres***, qui sont également traités dans cette rubrique.
- [Tableaux](arrays.md)
  - Un ***tableau*** est une structure de données contenant un certain nombre de variables accessibles par le biais d’indices calculés.
- [Interfaces](interfaces.md)
  - Une ***interface*** définit un contrat qui peut être implémenté par des classes et des structs. Une interface peut contenir des méthodes, des propriétés, des événements et des indexeurs. Une interface ne fournit pas d’implémentations des membres qu’elle définit ; elle spécifie simplement les membres qui doivent être fournis par les classes ou les structs qui implémentent l’interface.
- [Délégués](delegates.md)
  - Un ***type délégué*** représente des références à des méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont similaires au concept de pointeurs de fonction dans d’autres langages, mais, contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.
- [Attributs](attributes.md)
  - Les ***attributs*** permettent aux programmes de spécifier des informations déclaratives supplémentaires sur les types, les membres et d’autres entités.
  
> [!NOTE]
> Ces articles s’appliquent à C# 7,0 et versions ultérieures. Certaines fonctionnalités ne sont peut-être pas disponibles dans les versions antérieures.

> [!div class="step-by-step"]
> [Next](program-structure.md)
