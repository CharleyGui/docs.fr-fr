---
title: Visite guidée du langage C# - Guide du langage C#
description: Novice en matière de langage C# ? Découvrez les principes de base du langage.
ms.date: 02/26/2020
ms.openlocfilehash: bf5a200f2ee777698ae8564f348ffc117d9abab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79156842"
---
# <a name="a-tour-of-the-c-language"></a>Une visite de la langue C

CMD (prononcé « Voir Sharp ») est un langage de programmation moderne, orienté objet et sans danger pour le type. C# prend sa source dans la famille de langages C et sera immédiatement reconnaissable aux programmeurs en C, C++, Java et JavaScript.

Cette visite donne un aperçu des principales composantes de la langue dans C 8 et plus tôt. Si vous souhaitez explorer la langue à travers des exemples interactifs, essayez l’introduction aux tutoriels [C.](../tutorials/intro-to-csharp/index.md)

C# est un langage orienté objet, mais C# inclut de plus la prise en charge de la programmation ***orientée composant***. La conception logicielle moderne s’appuie de plus en plus sur les composants logiciels sous la forme de packages de fonctionnalités autonomes et autodescriptifs. La clé de ces composants est qu’ils présentent un modèle de programmation avec des propriétés, des méthodes et des événements. Ils ont des attributs qui fournissent des informations déclaratives sur le composant. Ils intègrent leur propre documentation. C fournit des constructions linguistiques pour soutenir directement ces concepts, faisant de C’un langage naturel dans lequel créer et utiliser des composants logiciels.

Plusieurs CMD aident à la construction d’applications robustes et durables. ***La collecte des ordures*** récupère automatiquement la mémoire occupée par des objets inutilisés inaccessibles. ***La manipulation d’exception*** fournit une approche structurée et extensible de la détection et de la récupération des erreurs. La conception sans type de la langue rend impossible la lecture à partir de variables uninitialisées, à indexer des tableaux ***au-delà*** de leurs limites, ou d’effectuer des moulages de type non contrôlés.

C# a un ***système de type unifié***. Tous les types C#, y compris les types primitifs tels que `int` et `double`, héritent d’un seul type `object` racine. Par conséquent, tous les types partagent un ensemble d’opérations communes, et des valeurs de tous types peuvent être stockées, transmises et exploitées de manière cohérente. En outre, C# prend en charge les types référence et les types valeur définis par l’utilisateur, ce qui permet l’allocation dynamique d’objets, ainsi que le stockage en ligne de structures légères.

Pour s’assurer que les programmes et les bibliothèques de Cmd peuvent évoluer au fil du temps d’une manière compatible, beaucoup d’accent a été mis sur ***la version*** dans la conception de C. De nombreux langages de programmation prêtent peu d’attention à cette question. Par conséquent, les programmes écrits dans ces autres langues se cassent plus souvent que nécessaire lorsque de nouvelles versions des bibliothèques dépendantes sont introduites. Les aspects de la conception de Cô qui ont `virtual` `override` été directement influencés par les considérations de version comprennent les éléments distincts et modificateurs, les règles de résolution de la surcharge de méthode et le soutien aux déclarations explicites des membres de l’interface.

Dans des versions plus récentes, C a adopté d’autres paradigmes de programmation. C a inclus des fonctionnalités qui prennent en charge les techniques de programmation fonctionnelles comme les expressions lambda. D’autres nouvelles fonctionnalités prennent en charge la séparation des données et des algorithmes, comme l’appariement des modèles.

## <a name="hello-world"></a>Hello World

Le programme « Hello, World » est souvent utilisé pour présenter un langage de programmation. Le voici en C# :

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

Les fichiers sources C# ont généralement l’extension de fichier `.cs`. Pour créer ce programme, téléchargez et installez d’abord le [.NET Core SDK](https://dotnet.microsoft.com/download). Ensuite, exécutez `dotnet new console -o hello` la commande pour créer un nouveau programme et un script de construction. Le programme et le script `Program.cs` `hello.csproj`de construction sont dans les fichiers et, respectivement. Vous construisez et exécutez l’application avec les `run` commandes :

```dotnetcli
cd hello
dotnet run
```

Le programme génère la sortie suivante :

```console
Hello, World!
```

Le programme « Hello, World » commence par une directive `using` qui fait référence à l’espace de noms `System`. Les espaces de noms représentent un moyen hiérarchique d’organiser les bibliothèques et les programmes C#. Les espaces de noms contiennent des types et d’autres espaces de noms ; par exemple, l’espace de noms `System` contient plusieurs types, notamment la classe `Console` référencée dans le programme, et d’autres espaces de noms, tels que `IO` et `Collections`. Une directive `using` qui fait référence à un espace de noms donné permet l’utilisation non qualifiée des types membres de cet espace de noms. En raison de la directive `using`, le programme peut utiliser `Console.WriteLine` comme raccourci pour `System.Console.WriteLine`.

La classe `Hello` déclarée par le programme « Hello, World » a un membre unique, la méthode nommée `Main`. La méthode `Main` est déclarée avec le modificateur statique. Si les méthodes d’instance peuvent faire référence à une instance d’objet englobante particulière avec le mot clé `this`, les méthodes statiques fonctionnent sans référence à un objet particulier. Par convention, une méthode statique nommée `Main` sert de point d’entrée d’un programme.

La sortie du programme est générée par la méthode `WriteLine` de la classe `Console` dans l’espace de noms `System`. Cette classe est fournie par les bibliothèques de classes standard, qui, par défaut, sont référencées automatiquement par le compilateur.

## <a name="elements-of-the-c-language"></a>Éléments de la langue C

Il y a beaucoup d’autres choses à apprendre sur C#. Les rubriques suivantes fournissent une vue d’ensemble des éléments du langage C#. Ces aperçus fournissent des informations de base sur tous les éléments de la langue et vous donnent les informations nécessaires pour plonger plus profondément :

- [Structure du programme](program-structure.md)
  - Découvrez les concepts clés d’organisation du langage C# : ***programmes***, ***espaces de noms***, ***types***, ***membres*** et ***assemblys***.
- [Types et variables](types-and-variables.md)
  - Découvrez les ***types valeur***, les ***types référence*** et les ***variables*** en langage C#.
- [Expressions](expressions.md)
  - Les ***expressions*** sont construites à partir de ***d’opérandes*** et ***d’opérateurs***. Les expressions produisent une valeur.
- [Déclarations](statements.md)
  - On utilise des ***instructions*** pour exprimer les actions d’un programme.
- [Classes et objets](classes-and-objects.md)
  - ***Les cours*** sont les plus fondamentaux des types de C. Les ***objets*** sont des instances d’une classe. Les classes sont générées à l’aide de ***membres***, qui sont également traités dans cette rubrique.
- [Tableaux](arrays.md)
  - Un ***tableau*** est une structure de données qui contient un certain nombre de variables qui sont accessibles par des indices calculés.
- [Interfaces](interfaces.md)
  - Une ***interface*** définit un contrat qui peut être implémenté par des classes et structures. Une interface peut contenir des méthodes, des propriétés, des événements et des indexeurs. Une interface ne fournit pas les implémentations des membres qu’elle définit, elle spécifie simplement les membres qui doivent être fournis par des classes ou des structs qui implémentent l’interface.
- [Délégués](delegates.md)
  - Un ***type délégué*** représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont similaires au concept de pointeurs de fonction dans d’autres langages, mais contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.
- [Attributs](attributes.md)
  - Les ***attributs*** permettent aux programmes de spécifier des informations déclaratives supplémentaires sur les types, les membres et d’autres entités.
  
> [!NOTE]
> Ces articles s’appliquent à C 7.0 et plus tard. Certaines fonctionnalités peuvent ne pas être disponibles dans les versions antérieures.

> [!div class="step-by-step"]
> [Suivant](program-structure.md)
