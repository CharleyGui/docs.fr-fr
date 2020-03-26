---
title: Introduction au langage C# et au .NET Framework
description: Apprenez les concepts de base de C# et .NET. Découvrez une vue d’ensemble du langage C# et de l’écosystème .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 828543b95ed82f465c92212748c6250b7fc84051
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249381"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Introduction à la langue C et au cadre .NET

C# est un langage élégant et de type sécurisé orienté objet qui permet aux développeurs de créer toute une gamme d’applications sûres et solides exécutées dans le .NET Framework. Vous pouvez utiliser C# pour créer des applications clientes Windows, services Web XML, composants distribués, applications client-serveur, applications de base de données et bien plus encore. Visual C# fournit un éditeur de code avancé, des concepteurs d’interface utilisateur pratiques, un débogueur intégré et de nombreux autres outils pour faciliter le développement d’applications basées sur le langage C# et le .NET Framework.  
  
> [!NOTE]
> La documentation de Visual C# suppose que vous avez une compréhension des concepts de base de la programmation. Si vous êtes un débutant complet, vous souhaiterez peut-être consulter Visual C# Express, qui est disponible sur le web. Vous pouvez également tirer parti de la documentation et des ressources Web sur C# pour acquérir des compétences de programmation pratiques.  
  
## <a name="c-language"></a>langage C#

La syntaxe C# est très expressive, mais elle est également simple et facile à apprendre. La syntaxe bouclée de Cmd sera immédiatement reconnaissable à toute personne familière avec C, C OU Java. Les développeurs qui connaissent un de ces langages peuvent généralement commencer à travailler efficacement en C# en très peu de temps. La syntaxe C simplifie bon nombre des complexités de la Cmd et fournit des caractéristiques puissantes telles que les types nuls, les énumérations, les délégués, les expressions lambda et l’accès direct à la mémoire. C# prend en charge des méthodes et types génériques qui fournissent de meilleures performances et plus de sécurité pour les types, et des itérateurs, qui permettent aux implémenteurs de classes de collection de définir des comportements d’itération personnalisés qui peuvent être utilisés facilement par le code client. Les expressions de requêtes intégrées par la langue (LINQ) font de la requête fortement tapée une construction linguistique de première classe.  
  
 En tant que langage orienté objet, C# prend en charge les concepts d’encapsulation, d’héritage et de polymorphisme. Toutes les variables et méthodes, y compris la méthode `Main`, le point d’entrée de l’application, sont encapsulées dans des définitions de classe. Une classe peut hériter directement d'une classe parent, mais peut implémenter un nombre quelconque d'interfaces. Les méthodes qui substituent des méthodes virtuelles dans une classe parente requièrent le mot-clé `override` pour éviter toute redéfinition accidentelle. En C#, un struct est comme une classe légère : il s’agit d’un type alloué par la pile qui peut implémenter des interfaces mais ne prend pas en charge l’héritage.  
  
 Outre ces principes orientés objet de base, C# facilite le développement de composants logiciels à travers plusieurs constructions de langage novatrices, y compris ce qui suit :  
  
- Des signatures de méthode encapsulées appelées *délégués*, qui activent les notifications d’événement de type sécurisé.  
  
- Les propriétés, qui sont utilisées comme accesseurs pour les variables de membre privé.  
  
- Les attributs, qui fournissent des métadonnées déclaratives sur les types au moment de l’exécution.  
  
- Commentaires de documentation XML inline.  
  
- Requête intégrée en langue (LINQ), qui offre des capacités de requête intégrées dans une variété de sources de données.  
  
 Si vous devez interagir avec d’autres logiciels Windows, comme des objets COM ou des DLL Win32 natives, vous pouvez pour cela utiliser un processus C# appelé « Interop ». L’interopérabilité permet aux programmes C# de faire presque tout ce qu’une application native C++ peut faire. C’prend même en charge les pointeurs et le concept de code "dangereux" pour les cas où l’accès direct à la mémoire est essentiel.  
  
 Le processus de génération de C# est simple par rapport à C et C++ et plus souple qu’avec Java. Il n’existe aucun fichier d’en-tête distinct, et les types et méthodes n’ont pas à être déclarés dans un ordre particulier. Un fichier source C# peut définir un nombre quelconque de classes, structs, interfaces et événements.  
  
 Voici des ressources C# supplémentaires :  
  
- Pour une bonne présentation générale du langage, consultez le chapitre 1 de la [Spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).  
  
- Pour plus d’informations sur des aspects spécifiques du langage C#, consultez la [Référence de C#](../language-reference/index.md).  
  
- Pour plus d’informations sur LINQ, voir [LINQ (Question intégrée des langues)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Architecture de la plateforme .NET Framework

 C# s’exécute sur le .NET Framework, un composant intégral de Windows qui inclut un système d’exécution virtuel appelé Common Language Runtime (CLR) et un ensemble unifié de bibliothèques de classes. CLR est l’implémentation commerciale par Microsoft de la Common Language Infrastructure (CLI), une norme internationale qui sert de base pour la création d’environnements de développement et d’exécution dans lesquels les langages et bibliothèques fonctionnent ensemble en toute transparence.  
  
 Le code source écrit dans le C est compilé dans une [langue intermédiaire (IL)](../../standard/managed-code.md) qui est conforme à la spécification CLI. Le code de langage intermédiaire et les ressources, comme les bitmaps et les chaînes, sont stockés sur disque dans un fichier exécutable appelé assembly, généralement avec l’extension .exe ou .dll. Un assembly contient un manifeste qui fournit des informations sur les types de l’assembly, sa version, sa culture et ses conditions de sécurité.  
  
 Lorsque le programme C# est exécuté, l’assembly est chargé dans CLR, qui peut prendre différentes mesures selon les informations contenues dans le manifeste. Ensuite, si les exigences de sécurité sont remplies, le CLR effectue la compilation Just-In-Time (JIT) pour convertir le code IL en instructions de machine native. CLR fournit également d’autres services connexes liés au nettoyage automatique de la mémoire (garbage collection), à la gestion des exceptions et à la gestion des ressources. Le code qui est exécuté par le CLR est parfois appelé «code géré», contrairement au «code non géré», qui est compilé dans la langue de la machine native qui cible un système spécifique. Le diagramme suivant illustre les relations de compilation et d’exécution des fichiers de code source de C#, les bibliothèques de classes .NET Framework, les assemblys et CLR.  
  
 ![Du code source C# à l'exécution machine](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 L’interopérabilité des langages est une fonctionnalité essentielle du .NET Framework. Étant donné que le code de langage intermédiaire produit par le compilateur C# est conforme à la spécification de type commun (CTS), le code de langage intermédiaire généré à partir de C# peut interagir avec du code qui a été généré à partir des versions .NET de Visual Basic, Visual C++ ou un des plus de 20 autres langages compatibles CTS. Un seul assembly peut contenir plusieurs modules écrits dans différents langages .NET, et les types peuvent se référencent mutuellement comme s’ils avaient été écrits dans la même langue.  
  
 Outre les services de runtime, le .NET Framework inclut également une bibliothèque étendue de plus de 4 000 classes organisées en espaces de noms qui fournissent une grande variété de fonctionnalités utiles pour tous les éléments allant de l’entrée et la sortie de fichiers pour la manipulation de chaînes à l’analyse de XML, en passant par les contrôles Windows Forms. Une application C# standard utilise la bibliothèque de classes du .NET Framework de façon intensive pour gérer les tâches fastidieuses.  
  
 Pour plus d’informations sur .NET Framework, consultez [Présentation de Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Mise en route de Visual C#](/visualstudio/ide/quickstart-csharp-console)
