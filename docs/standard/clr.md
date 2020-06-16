---
title: Vue d’ensemble du Common Language Runtime (CLR) - .NET Framework
description: Prise en main de common language runtime (CLR), l’environnement d’exécution .NET. Le CLR exécute du code et fournit des services pour faciliter le processus de développement.
ms.date: 04/02/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
ms.custom: updateeachrelease
ms.openlocfilehash: ef455ac1c49c1f457d0fa432db91b5375c045840
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769208"
---
# <a name="common-language-runtime-clr-overview"></a>Vue d’ensemble du Common Language Runtime (CLR)

Le .NET Framework fournit un environnement d'exécution, appelé le Common Language Runtime, qui exécute le code et offre des services qui simplifient le processus de développement.

Les compilateurs et les outils exposent le fonctionnement du Common Language Runtime et vous permettent d'écrire du code qui bénéficie de cet environnement d'exécution managée. Le code que vous développez à l'aide d'un compilateur de langage ciblant le runtime est appelé code managé ; il tire parti de fonctionnalités telles que l'intégration interlangage, la gestion interlangage des exceptions, la sécurité améliorée, la prise en charge du versioning et du déploiement, un modèle simplifié de l'interaction des composants, ainsi que des services de débogage et de gestion de profils.

> [!NOTE]
> Les compilateurs et les outils peuvent générer une sortie que le Common Language Runtime peut consommer parce que le système de type, le format des métadonnées et l'environnement d'exécution (système d'exécution virtuel) sont tous définis par une norme publique, la spécification CLI (Common Language Infrastructure) ECMA. Pour plus d’informations, consultez [ECMA C# and Common Language Infrastructure Specifications](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/) (Spécifications CLI et ECMA C#).

Pour permettre au runtime de fournir des services au code managé, les compilateurs de langage doivent générer des métadonnées qui décrivent les types, les membres et les références de votre code. Les métadonnées sont stockées avec le code ; chaque fichier exécutable portable (PE) chargeable du Common Language Runtime contient des métadonnées. Le runtime utilise les métadonnées pour rechercher et charger des classes, placer des instances en mémoire, résoudre des appels de méthode, générer un code natif, appliquer la sécurité et définir les limites du contexte d'exécution.

Le runtime gère automatiquement la disposition des objets et manage les références aux objets, les libérant quand ils ne sont plus utilisés. Les objets dont la durée de vie est managée de cette façon sont appelés données managées. Le garbage collection élimine les fuites de mémoire ainsi que d'autres erreurs de programmation courantes. Si votre code est managé, vous pouvez utiliser des données managées, des données non managées, ou à la fois des données managées et non managées dans votre application .NET Framework. Dans la mesure où les compilateurs de langage fournissent leurs propres types, tels que des types primitifs, vous ne pouvez pas toujours savoir (ou avoir besoin de savoir) si vos données sont managées.

Le Common Language Runtime facilite la conception de composants et d'applications dont les objets interagissent entre les langages. Les objets écrits dans des langages différents peuvent communiquer les uns avec les autres, et leurs comportements peuvent être fortement intégrés. Par exemple, vous pouvez définir une classe puis utiliser un langage différent pour dériver une classe de votre classe d'origine ou appeler une méthode pour la classe d'origine. Vous pouvez également passer une instance d'une classe à une méthode d'une classe écrite dans un autre langage. Cette intégration interlangage n'est possible que parce que les outils et les compilateurs de langage ciblant le runtime utilisent un système de type commun défini par le runtime, et qu'ils suivent les règles établies par le runtime en matière de définition de nouveaux types, ainsi que de création, d'utilisation, de persistance de types et de liaison avec ceux-ci.

Au sein de leurs métadonnées, tous les composants managés comportent des informations relatives aux composants et aux ressources pour lesquels ils ont été générés. Le runtime exploite ces informations pour s'assurer que votre composant ou application possède les versions spécifiées de tous les éléments dont il a besoin, ce qui rend votre code moins enclin aux arrêts provoqués par une dépendance sans correspondance. Les informations d'inscription et les données d'état ne sont plus stockées dans le Registre où il peut être difficile de les implanter et de les gérer. Au lieu de cela, les informations relatives aux types que vous définissez (et leurs dépendances) sont stockées avec le code en tant que métadonnées, rendant les tâches de réplication et de suppression de composants beaucoup moins compliquées.

Les outils et les compilateurs de langage exposent le fonctionnement du runtime selon des modes qui se veulent utiles et intuitifs pour les développeurs. Cela signifie que certaines fonctionnalités du runtime peuvent se faire remarquer davantage dans un environnement que dans un autre. Les fonctionnalités du runtime dépend des compilateurs de langage ou des outils utilisés. Par exemple, si vous êtes un développeur Visual Basic, vous pouvez remarquer qu'avec le Common Language Runtime, le langage Visual Basic dispose davantage de fonctionnalités orientées objet qu'avant. Le runtime fournit les avantages suivants :

- Amélioration des performances.

- Possibilité d'utiliser facilement des composants développés dans d'autres langages.

- Types extensibles fournis par une bibliothèque de classes.

- Fonctionnalités de langage telles que l'héritage, les interfaces et la surcharge pour la programmation orientée objet.

- Prise en charge du modèle de thread libre explicite qui permet la création d'applications évolutives multithread.

- Prise en charge de la gestion structurée des exceptions.

- Prise en charge des attributs personnalisés.

- Garbage collection.

- Utilisation des délégués plutôt que des pointeurs fonction pour une sécurité de type et une sécurité accrues. Pour plus d'informations sur les délégués, consultez [Système de type commun](base-types/common-type-system.md).

## <a name="clr-versions"></a>Versions CLR

Le numéro de version de .NET Framework ne correspond pas nécessairement au numéro de version du CLR qu’il contient. Pour obtenir la liste des versions de .NET Framework et leurs versions CLR correspondantes, consultez [versions et dépendances de .NET Framework](../framework/migration-guide/versions-and-dependencies.md). Les versions de .NET Core ont une seule version de produit, autrement dit, il n’existe pas de version CLR distincte. Pour obtenir la liste des versions de .NET Core, consultez [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Processus d’exécution managée](managed-execution-process.md)|Décrit les étapes nécessaires pour tirer parti du Common Language Runtime.|
|[Gestion automatique de la mémoire](automatic-memory-management.md)|Explique comment le « garbage collector » alloue et libère la mémoire.|
|[Vue d’ensemble de l' .NET Framework](../framework/get-started/overview.md)|Décrit les concepts fondamentaux du .NET Framework, tels que le système de type commun (CTS, Common Type System), l'interopérabilité interlangage, l'exécution managée, les domaines d'application et les assemblys.|
|[Système de type commun](./base-types/common-type-system.md)|Décrit la manière dont les types sont déclarés, utilisés et managés dans le runtime à l'appui de l'intégration interlangage.|
