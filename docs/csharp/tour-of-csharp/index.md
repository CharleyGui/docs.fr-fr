---
title: Visite guidée du langage C# - Guide du langage C#
description: Novice en matière de langage C# ? Découvrez les principes de base du langage.
ms.date: 02/26/2020
ms.openlocfilehash: 7476356ceab39d5cccb6ccbeb991653f08a324ea
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141045"
---
# <a name="a-tour-of-the-c-language"></a>Visite guidée du langage C#

C# (prononcé « voir Sharp ») est un langage de programmation moderne, orienté objet et de type sécurisé. C# prend sa source dans la famille de langages C et sera immédiatement reconnaissable aux programmeurs en C, C++, Java et JavaScript.

Cette visite guidée fournit une vue d’ensemble des principaux composants du langage dans C# 8 et versions antérieures. Si vous souhaitez explorer le langage par le biais d’exemples interactifs, consultez la présentation des didacticiels [C#](../tutorials/intro-to-csharp/index.md) .

C# est un langage orienté objet, mais C# inclut de plus la prise en charge de la programmation ***orientée composant***. La conception logicielle moderne s’appuie de plus en plus sur les composants logiciels sous la forme de packages de fonctionnalités autonomes et autodescriptifs. La clé de ces composants est qu’ils présentent un modèle de programmation avec des propriétés, des méthodes et des événements. Ils ont des attributs qui fournissent des informations déclaratives sur le composant. Ils intègrent leur propre documentation. C# fournit des constructions de langage pour prendre en charge directement ces concepts, en faisant de C# un langage naturel dans lequel créer et utiliser des composants logiciels.

Plusieurs fonctionnalités C# vous aident à construire des applications robustes et durables. Le ***garbage collection*** libère automatiquement la mémoire occupée par des objets inutilisés inaccessibles. La ***gestion des exceptions*** offre une approche structurée et extensible de la détection et de la récupération des erreurs. La conception de ***type sécurisé*** du langage rend impossible la lecture des variables non initialisées, l’indexation des tableaux au-delà de leurs limites ou l’exécution de conversions de type non vérifiées.

C# a un ***système de type unifié***. Tous les types C#, y compris les types primitifs tels que `int` et `double`, héritent d’un seul type `object` racine. Par conséquent, tous les types partagent un ensemble d’opérations communes, et des valeurs de tous types peuvent être stockées, transmises et exploitées de manière cohérente. En outre, C# prend en charge les types référence et les types valeur définis par l’utilisateur, ce qui permet l’allocation dynamique d’objets, ainsi que le stockage en ligne de structures légères.

Pour vous assurer que les bibliothèques et les programmes C# peuvent évoluer au fil du temps d’une manière compatible, l’accent est mis sur le contrôle de ***version*** dans la conception de c#. De nombreux langages de programmation ne sont pas très attentifs à ce problème. Par conséquent, les programmes écrits dans ces autres langages s’arrêtent plus souvent que nécessaire lorsque des versions plus récentes des bibliothèques dépendantes sont introduites. Les aspects de la conception de C# qui ont été directement influencés par les considérations `virtual` relatives `override` à la gestion des versions incluent les modificateurs et séparés, les règles de résolution de surcharge de méthode et la prise en charge des déclarations de membres d’interface explicites.

Dans les versions plus récentes, C# a adopté d’autres paradigmes de programmation. C# a inclus des fonctionnalités qui prennent en charge des techniques de programmation fonctionnelle comme les expressions lambda. D’autres nouvelles fonctionnalités prennent en charge la séparation des données et des algorithmes, comme les critères spéciaux.

## <a name="hello-world"></a>Hello World

Le programme « Hello, World » est souvent utilisé pour présenter un langage de programmation. Le voici en C# :

[!code-csharp[Hello World](~/samples/snippets/csharp/tour/hello/Program.cs)]

Les fichiers sources C# ont généralement l’extension de fichier `.cs`. Pour créer ce programme, commencez par télécharger et installer le [Kit SDK .net Core](https://dotnet.microsoft.com/download). Ensuite, exécutez la commande `dotnet new console -o hello` pour créer un nouveau programme et un script de génération. Le programme et le script de compilation se trouvent `Program.cs` dans `hello.csproj`les fichiers et, respectivement. Vous générez et exécutez l’application avec `run` les commandes suivantes :

```dotnetcli
cd hello
dotnet run
```

Le programme génère la sortie suivante :

```dotnetcli
Hello, World!
```

Le programme « Hello, World » commence par une directive `using` qui fait référence à l’espace de noms `System`. Les espaces de noms représentent un moyen hiérarchique d’organiser les bibliothèques et les programmes C#. Les espaces de noms contiennent des types et d’autres espaces de noms ; par exemple, l’espace de noms `System` contient plusieurs types, notamment la classe `Console` référencée dans le programme, et d’autres espaces de noms, tels que `IO` et `Collections`. Une directive `using` qui fait référence à un espace de noms donné permet l’utilisation non qualifiée des types membres de cet espace de noms. En raison de la directive `using`, le programme peut utiliser `Console.WriteLine` comme raccourci pour `System.Console.WriteLine`.

La classe `Hello` déclarée par le programme « Hello, World » a un membre unique, la méthode nommée `Main`. La méthode `Main` est déclarée avec le modificateur statique. Si les méthodes d’instance peuvent faire référence à une instance d’objet englobante particulière avec le mot clé `this`, les méthodes statiques fonctionnent sans référence à un objet particulier. Par convention, une méthode statique nommée `Main` sert de point d’entrée d’un programme.

La sortie du programme est générée par la méthode `WriteLine` de la classe `Console` dans l’espace de noms `System`. Cette classe est fournie par les bibliothèques de classes standard, qui, par défaut, sont référencées automatiquement par le compilateur.

## <a name="elements-of-the-c-language"></a>Éléments du langage C#

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
  - Les ***classes*** sont les plus fondamentales des types de C#. Les ***objets*** sont des instances d’une classe. Les classes sont générées à l’aide de ***membres***, qui sont également traités dans cette rubrique.
- [Tableaux](arrays.md)
  - Un ***tableau*** est une structure de données qui contient un certain nombre de variables qui sont accessibles par des indices calculés.
- [Interfaces](interfaces.md)
  - Une ***interface*** définit un contrat qui peut être implémenté par des classes et structures. Une interface peut contenir des méthodes, des propriétés, des événements et des indexeurs. Une interface ne fournit pas d’implémentations des membres qu’elle définit ; elle spécifie simplement les membres qui doivent être fournis par les classes ou les structs qui implémentent l’interface.
- [Délégués](delegates.md)
  - Un ***type délégué*** représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont similaires au concept de pointeurs de fonction dans d’autres langages, mais contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.
- [Attributs](attributes.md)
  - Les ***attributs*** permettent aux programmes de spécifier des informations déclaratives supplémentaires sur les types, les membres et d’autres entités.
  
> [!NOTE]
> Ces articles s’appliquent à C# 7,0 et versions ultérieures. Certaines fonctionnalités ne sont peut-être pas disponibles dans les versions antérieures.

> [!div class="step-by-step"]
> [Suivant](program-structure.md)
