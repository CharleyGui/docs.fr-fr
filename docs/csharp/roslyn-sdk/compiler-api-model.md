---
title: Concepts et modèle objet du SDK .NET Compiler Platform
description: Cette présentation fournit les informations dont vous avez besoin pour utiliser efficacement le SDK .NET Compiler Platform. Vous allez découvrir les différentes couches d’API, les principaux types utilisés et le modèle objet global.
ms.date: 07/13/2020
ms.custom: mvc
ms.openlocfilehash: f4b2163c3bf8824b6ad93f0b144a6b02d870f50a
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899163"
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>Comprendre le modèle du SDK .NET Compiler Platform

Les compilateurs traitent le code que vous écrivez en suivant des règles structurées qui diffèrent souvent de la façon dont vous pouvez vous-même lire et comprendre le code. Pour bien comprendre le fonctionnement des API dont vous avez besoin pour créer des outils Roslyn, vous devez connaître les concepts de base du modèle utilisé par les compilateurs.

## <a name="compiler-pipeline-functional-areas"></a>Zones fonctionnelles du pipeline de compilateur

Le SDK .NET Compiler Platform expose les analyses de code des compilateurs C# et Visual Basic en vous fournissant, en tant que consommateur, une couche d’API qui reflète un pipeline de compilateur standard.

![étapes du pipeline de compilateur pour traiter le code source en code objet](media/compiler-api-model/compiler-pipeline.png)

Chaque phase de ce pipeline correspond à un composant distinct. Tout d’abord, la phase d’analyse segmente et analyse le texte source dans la syntaxe grammaticale du langage utilisé. Ensuite, la phase de déclaration analyse les métadonnées sources et importées pour former des symboles nommés. Après cela, la phase de liaison mappe les identificateurs dans le code à des symboles. Enfin, la phase d’émission émet un assembly qui contient toutes les informations générées par le compilateur.

![L’API du pipeline du compilateur fournit l’accès à chaque étape du pipeline du compilateur](media/compiler-api-model/compiler-pipeline-api.png)

Pour chacune de ces phases, le SDK .NET Compiler Platform expose un modèle objet qui permet d’accéder aux informations disponibles à la phase en question. La phase d’analyse expose une arborescence de syntaxe, la phase de déclaration expose une table de symboles hiérarchique, la phase de liaison expose le résultat de l’analyse sémantique du compilateur, et la phase d’émission est une API qui produit des codes d’octet de langage intermédiaire.

![services de langage disponibles à partir de l’API du compilateur à chaque phase du pipeline du compilateur](media/compiler-api-model/compiler-pipeline-lang-svc.png)

Chaque compilateur combine ces composants en une solution de bout en bout unique.

Ces API sont les mêmes que celles utilisées par Visual Studio. Par exemple, les fonctionnalités de mise en forme et de mise en forme du code utilisent les arborescences de syntaxe, l' **Explorateur d’objets** et les fonctionnalités de navigation utilisent la table de symboles, les refactorisations et **atteindre la définition** utilisent le modèle sémantique, et **Modifier & Continuer** utilise tous ces éléments, y compris l’API d’émission.

## <a name="api-layers"></a>Couches d’API

Le SDK du compilateur .NET est constitué de plusieurs couches d’API : les API du compilateur, les API de diagnostic, les API de script et les API d’espaces de travail.

### <a name="compiler-apis"></a>API du compilateur

La couche du compilateur contient les modèles objet qui correspondent aux informations syntaxiques et sémantiques exposées à chaque phase du pipeline du compilateur. La couche du compilateur contient également un instantané immuable d’un appel unique d’un compilateur, notamment les références d’assembly, les options du compilateur et les fichiers de code source. Le langage C# et le langage Visual Basic sont représentés par deux API distinctes. Les deux API sont similaires, mais elles sont adaptées à une haute fidélité pour chaque langue. Cette couche n’a pas de dépendances sur les composants Visual Studio.

### <a name="diagnostic-apis"></a>API de diagnostic

Dans le cadre de son analyse, le compilateur peut générer un ensemble de diagnostics couvrant tout, des erreurs de syntaxe, de sémantique et d’assignation définie à divers avertissements et diagnostics d’informations. La couche API du compilateur expose les diagnostics par le biais d’une API extensible qui permet d’intégrer des analyseurs définis par l’utilisateur au processus de compilation. Il permet aux diagnostics définis par l’utilisateur, tels que ceux générés par des outils tels que StyleCop, de se produire avec les diagnostics définis par le compilateur. La production de diagnostics de cette façon présente l’avantage d’intégrer naturellement des outils tels que MSBuild et Visual Studio, qui dépendent des diagnostics pour des expériences telles que l’arrêt d’une build basée sur la stratégie et l’affichage des tildes dynamiques dans l’éditeur et la suggestion de correction de code.

### <a name="scripting-apis"></a>API de script

Les API d’hébergement et de script font partie de la couche du compilateur. Vous pouvez utiliser ces API pour l’exécution d’extraits de code et l’accumulation d’un contexte d’exécution du runtime.
Le REPL (Read-Evaluate-Print Loop) interactif C# utilise ces API. Le REPL vous permet d’utiliser C# comme langage de script, en exécutant le code que vous écrivez de manière interactive.

### <a name="workspaces-apis"></a>API des espaces de travail

La couche des espaces de travail contient les API des espaces de travail, à partir desquelles sont effectuées les analyses de code et la refactorisation dans les solutions entières. Il vous aide à organiser toutes les informations sur les projets d’une solution en un modèle d’objet unique, vous offrant un accès direct aux modèles d’objet de la couche du compilateur sans avoir à analyser des fichiers, configurer des options ou gérer des dépendances entre projets.

De plus, la couche des espaces de travail expose un ensemble d’API utilisées pour l’implémentation d’outils d’analyse du code et de refactorisation qui fonctionnent dans un environnement hôte, tel que l’IDE Visual Studio. Les API Rechercher toutes les références, Mise en forme et Génération de code en sont des exemples.

Cette couche n’a pas de dépendances sur les composants Visual Studio.
