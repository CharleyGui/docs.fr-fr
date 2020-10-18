---
title: Commencez-présentation du langage C# et de .NET»
description: Apprenez les concepts de base de C# et .NET. Découvrez une vue d’ensemble du langage C# et de l’écosystème .NET.
ms.date: 10/13/2020
ms.openlocfilehash: 94d49be28fbdba8f58ca16e959a10643d6467c63
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160956"
---
# <a name="introduction-to-the-c-language-and-net"></a>Introduction au langage C# et à .NET

C# est un langage orienté objet élégant et de type sécurisé. C# permet aux développeurs de créer de nombreux types d’applications sécurisées et fiables qui s’exécutent dans l’écosystème .NET.

## <a name="c-language"></a>langage C#

La syntaxe C# est très expressif, mais elle est également simple et facile à apprendre. La syntaxe de l’accolade de C# sera immédiatement reconnaissable à toute personne connaissant le langage C, C++, Java ou JavaScript. Les développeurs qui connaissent l’un de ces langages sont généralement en mesure de travailler de manière productive en C# dans un laps de temps. C# fournit des fonctionnalités puissantes telles que les types Nullable, les délégués, les expressions lambda, les critères spéciaux et l’accès direct à la mémoire sécurisée. C# prend en charge des méthodes et des types génériques, ce qui améliore la sécurité et les performances de type. C# fournit des itérateurs, qui permettent aux implémenteurs de classes de collection de définir des comportements personnalisés pour le code client. Les expressions LINQ (Language-Integrated Query) font de la requête fortement typée une construction de langage de première classe.

En tant que langage orienté objet, C# prend en charge les concepts d’encapsulation, d’héritage et de polymorphisme. Une classe peut hériter directement d'une classe parent, mais peut implémenter un nombre quelconque d'interfaces. Les méthodes qui substituent des méthodes virtuelles dans une classe parente requièrent le mot-clé `override` pour éviter toute redéfinition accidentelle. En C#, un struct est semblable à une classe légère ; Il s’agit d’un type alloué par la pile qui peut implémenter des interfaces mais ne prend pas en charge l’héritage. C# fournit également des enregistrements, qui sont des types de classe dont l’objectif est principalement le stockage des valeurs de données.

C# facilite le développement de composants logiciels à travers plusieurs constructions de langage innovantes, notamment :

- Des signatures de méthode encapsulées appelées *délégués*, qui activent les notifications d’événement de type sécurisé.
- Les propriétés, qui sont utilisées comme accesseurs pour les variables de membre privé.
- Les attributs, qui fournissent des métadonnées déclaratives sur les types au moment de l’exécution.
- Commentaires de documentation XML inline.
- Language-Integrated query (LINQ), qui fournit des fonctionnalités de requête intégrées sur différents types de sources de données.
- Critères spéciaux, qui permettent de contrôler le workflow en inspectant les types de données et les valeurs.

Vous interagissez avec les composants natifs à l’aide d’un processus appelé « Interop ». L’interopérabilité permet aux programmes C# de faire presque tout ce qu’une application native C++ peut faire. C# prend même en charge les pointeurs et le concept de code « unsafe » dans les cas où l’accès direct à la mémoire est essentiel.

Le processus de génération de C# est simple par rapport à C et C++ et plus souple qu’avec Java. Il n’existe aucun fichier d’en-tête distinct, et les types et méthodes n’ont pas à être déclarés dans un ordre particulier. Un fichier source C# peut définir un nombre quelconque de classes, structs, interfaces et événements.

Voici des ressources C# supplémentaires :

- Pour une bonne présentation générale du langage, consultez la [visite guidée de C#](../tour-of-csharp/index.md).
- Pour plus d’informations sur des aspects spécifiques du langage C#, consultez la [Référence de C#](../language-reference/index.md).
- Pour plus d’informations sur LINQ, consultez [LINQ (Language-Integrated Query)](../programming-guide/concepts/linq/index.md).

## <a name="net-platform-architecture"></a>Architecture de la plateforme .NET

Les programmes C# s’exécutent sur .NET, un système d’exécution virtuel appelé le common language runtime (CLR) et un ensemble unifié de bibliothèques de classes. Le CLR est l’implémentation commerciale de Microsoft de l’infrastructure de langage commun (CLI), une norme internationale. L’interface CLI est la base de la création d’environnements d’exécution et de développement dans lesquels les langages et les bibliothèques fonctionnent ensemble de façon transparente.

Le code source écrit en C# est compilé dans un [langage intermédiaire (il)](../../standard/managed-code.md) conforme à la spécification CLI. Le code de langage intermédiaire et les ressources, telles que les bitmaps et les chaînes, sont stockés dans un assembly, généralement avec une extension. dll. Un assembly contient un manifeste qui fournit des informations sur les types, la version et la culture de l’assembly.

Lorsque le programme C# est exécuté, l’assembly est chargé dans le CLR. Le CLR effectue une compilation juste-à-temps (JIT) pour convertir le code de langage intermédiaire en instructions machine natives. Le CLR fournit d’autres services liés à la garbage collection automatique, à la gestion des exceptions et à la gestion des ressources. Le code exécuté par le CLR est parfois appelé « code managé », contrairement à « code non managé », qui est compilé dans un langage machine natif ciblant un système spécifique.

L’interopérabilité des langages est une fonctionnalité clé de .NET. Le code de langage intermédiaire produit par le compilateur C# est conforme à la spécification de type commun (CTS). Le code de langage intermédiaire généré à partir de C# peut interagir avec le code généré à partir des versions .NET de F #, Visual Basic, C++ ou l’un des plus de 20 autres langages compatibles CTS. Un seul assembly peut contenir plusieurs modules écrits dans différents langages .NET, et les types peuvent se référencer mutuellement comme s’ils avaient été écrits dans le même langage.

Outre les services d’exécution, .NET comprend également des bibliothèques étendues. Ces bibliothèques prennent en charge de nombreuses charges de travail différentes. Elles sont organisées en espaces de noms qui fournissent un large éventail de fonctionnalités utiles pour tout, de l’entrée de fichier à la sortie de la manipulation de chaînes à l’analyse XML, aux infrastructures d’application Web pour Windows Forms contrôles. L’application C# classique utilise largement la bibliothèque de classes .NET pour gérer les tâches courantes de « plomberie ».

Pour plus d’informations sur .NET, consultez [vue d’ensemble de .net](../../core/introduction.md).
