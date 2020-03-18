---
title: 'Mettre à jour en toute sécurité les interfaces à l’aide de méthodes d’interface par défaut dans C #'
description: Ce tutoriel avancé explore comment vous pouvez ajouter de manière sécurisée de nouvelles fonctionnalités aux définitions d’une interface existante sans rompre toutes les classes et tous les structs qui implémentent cette interface.
ms.date: 05/06/2019
ms.technlogy: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: 650aea78b421783b3f249b3670578aa60e800ab2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156777"
---
# <a name="tutorial-update-interfaces-with-default-interface-methods-in-c-80"></a>Tutorial : Mettre à jour les interfaces avec les méthodes d’interface par défaut dans C 8.0

Depuis C# 8.0 sur .NET Core 3.0, vous pouvez définir une implémentation lorsque vous déclarez un membre d’une interface. Le scénario le plus courant consiste à ajouter de manière sécurisée des membres à une interface déjà publiée et utilisée par de nombreux clients.

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> * Étendre des interfaces de manière sécurisée en ajoutant des méthodes avec des implémentations
> * Créer des implémentations paramétrables pour fournir une plus grande flexibilité
> * Permettre aux implémenteurs de fournir une implémentation plus spécifique sous la forme d’un remplacement

## <a name="prerequisites"></a>Conditions préalables requises

Vous aurez besoin de configurer votre machine pour exécuter .NET Core, y compris le compilateur C 8.0. Le compilateur C 8.0 est disponible à partir de [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou le [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).

## <a name="scenario-overview"></a>Présentation du scénario

Ce tutoriel commence par la version 1 d’une bibliothèque de relation client. Vous pouvez obtenir l’application de démarrage à partir de notre [dépôt samples sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship). L’entreprise qui a créé cette bibliothèque espérait la voir adoptée par les clients ayant des applications existantes. Elle a fourni des définitions d’interface minimales destinées à être implémentées par les utilisateurs de sa bibliothèque. Voici la définition d’interface pour un client :

[!code-csharp[InitialCustomerInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Elle a défini une deuxième interface qui représente une commande :

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

À partir de ces interfaces, l’équipe a pu générer une bibliothèque pour les utilisateurs permettant de créer une meilleure expérience pour ses clients. Son objectif était de créer une relation plus étroite avec les clients existants et d’améliorer ses relations avec les nouveaux clients.

À présent, il est temps de mettre à niveau la bibliothèque pour la prochaine version. L’une des fonctionnalités demandées permet une remise de fidélité pour les clients qui ont un grand nombre de commandes. Cette nouvelle remise de fidélité est appliquée chaque fois qu’un client passe une commande. La remise spécifique est une propriété de chaque client. Chaque mise `ICustomer` en œuvre peut établir des règles différentes pour la remise de fidélité.

La façon la plus naturelle d’ajouter cette fonctionnalité consiste à améliorer l’interface `ICustomer` avec une méthode pour appliquer une remise de fidélité. Cette suggestion de conception a suscité l’inquiétude des développeurs expérimentés : « Les interfaces sont immuables une fois qu’elles ont été libérées ! Il s’agit d’une modification avec rupture ! » C# 8.0 ajoute des *implémentations d’interface par défaut* pour la mise à niveau des interfaces. Les auteurs de bibliothèque peuvent ajouter de nouveaux membres à l’interface et fournir une implémentation par défaut pour ces membres.

Les implémentations d’interface par défaut permettent aux développeurs de mettre à niveau une interface tout en laissant la possibilité aux implémenteurs de substituer cette implémentation. Les utilisateurs de la bibliothèque peuvent accepter l’implémentation par défaut en tant que modification sans rupture. Si leurs règles métier sont différentes, ils peuvent opérer un remplacement.

## <a name="upgrade-with-default-interface-methods"></a>Mise à niveau avec des méthodes d’interface par défaut

L’équipe s’est mise d’accord sur l’implémentation par défaut la plus vraisemblable : une remise de fidélité pour les clients.

La mise à niveau doit fournir la fonctionnalité permettant de définir deux propriétés : le nombre de commandes nécessaires pour pouvoir bénéficier de la remise et le pourcentage de celle-ci. Cela en fait un scénario parfait pour les méthodes d’interface par défaut. Vous pouvez ajouter une `ICustomer` méthode à l’interface et fournir la mise en œuvre la plus probable. Toutes les implémentations existantes et nouvelles peuvent utiliser l’implémentation par défaut ou fournir la leur.

Tout d’abord, ajoutez la nouvelle méthode à l’implémentation :

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

L’auteur de la bibliothèque a écrit un premier test pour vérifier l’implémentation :

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Notez la partie suivante du test :

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

Ce cast de `SampleCustomer` en `ICustomer` est nécessaire. La classe `SampleCustomer` n’a pas besoin de fournir une implémentation pour `ComputeLoyaltyDiscount` ; elle est fournie par l’interface `ICustomer`. Toutefois, la classe `SampleCustomer` n’hérite pas les membres de ses interfaces. Cette règle n’a pas changé. Pour qu’il soit possible d’appeler n’importe quelle méthode déclarée et implémentée dans l’interface, la variable doit être du même type que l’interface, `ICustomer` dans cet exemple.

## <a name="provide-parameterization"></a>Fournir le paramétrage

C’est un bon début. Toutefois, l’implémentation par défaut est trop restrictive. De nombreux consommateurs de ce système peuvent choisir des seuils différents pour le nombre d’achats, une durée différente pour la qualité de membre ou un pourcentage de remise différent. Vous pouvez procurer une meilleure expérience de mise à niveau à davantage de clients en fournissant un moyen de définir ces paramètres. Nous allons ajouter une méthode statique qui définit ces trois paramètres de contrôle de l’implémentation par défaut :

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Il existe de nombreuses nouvelles capacités linguistiques dans ce petit fragment de code. Les interfaces peuvent maintenant inclure des membres statiques, notamment des champs et des méthodes. Différents modificateurs d’accès sont également activés. Les champs supplémentaires sont privés, tandis que la nouvelle méthode est publique. Tout modificateur est autorisé sur les membres d’interface.

Les applications qui utilisent la formule générale pour le calcul de la remise de fidélité, mais des paramètres différents, n’ont pas besoin de fournir une implémentation personnalisée ; elles peuvent définir les arguments par le biais d’une méthode statique. Par exemple, le code suivant définit une « évaluation du client » qui récompense tout client membre depuis plus d’un mois :

[!code-csharp[SetLoyaltyThresholds](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Étendre l’implémentation par défaut

Le code que vous avez ajouté jusqu’à présent a fourni une implémentation pratique pour les scénarios où les utilisateurs veulent quelque chose comme l’implémentation par défaut ou pour fournir un ensemble de règles non lié. En guise de dernière fonctionnalité, nous allons refactoriser le code un peu pour permettre les scénarios où les utilisateurs sont susceptibles de vouloir générer l’implémentation par défaut.

Imaginez une start-up qui souhaite attirer de nouveaux clients. Elle offre une remise de 50 % sur la première commande d’un nouveau client. Pour leur part, les clients existants bénéficient de la remise standard. L’auteur de la bibliothèque doit déplacer l’implémentation par défaut vers une méthode `protected static` afin que toute classe qui implémente cette interface puisse réutiliser le code dans son implémentation. L’implémentation par défaut du membre d’interface appelle également cette méthode partagée :

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

Dans une implémentation d’une classe qui implémente cette interface, le remplacement peut appeler la méthode d’assistance statique et étendre cette logique pour fournir la remise « nouveau client » :

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Vous pouvez voir l’intégralité du code terminé dans notre [dépôt d’exemples sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship). Vous pouvez obtenir l’application de démarrage à partir de notre [dépôt samples sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship).

Ces nouvelles fonctionnalités signifient que les interfaces peuvent être mises à jour de manière sécurisée quand il existe une implémentation par défaut raisonnable pour les nouveaux membres. Concevez soigneusement les interfaces pour exprimer des idées fonctionnelles uniques pouvant être implémentées par plusieurs classes. Cela facilite la mise à niveau de ces définitions d’interface quand de nouvelles exigences sont découvertes pour cette même idée fonctionnelle.
