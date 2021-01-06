---
title: Prise en main d’Azure et .NET
description: Découvrez les principes de base que vous devez savoir sur Azure et .NET.
ms.date: 06/20/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 5d14bd0d9930d41a8c60b58b9f5b0522f0c0e398
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700771"
---
# <a name="introduction-to-azure-and-net"></a>Présentation d’Azure et de .NET

## <a name="what-is-azure"></a>Qu’est-ce qu’Azure ?

Azure est une plateforme Cloud conçue pour simplifier le processus de création d’applications modernes.  Que vous choisissiez d’héberger vos applications entièrement dans Azure ou d’étendre vos applications locales avec des services Azure, Azure vous aide à créer des applications évolutives, fiables et gérables.  Grâce à la prise en charge étendue des outils que vous utilisez déjà comme Visual Studio et Visual Studio Code et d’une bibliothèque de SDK complète, Azure est conçu pour vous permettre de développer le développement .NET dès le départ.

## <a name="application-development-scenarios-on-azure"></a>Scénarios de développement d’applications sur Azure

Vous pouvez incorporer Azure à votre application de différentes façons en fonction de vos besoins.

- **Hébergement d’applications sur Azure-** Azure peut héberger la totalité de votre pile d’applications à partir d’applications Web et d’API vers des bases de données vers des services de stockage. Azure prend en charge un large éventail de modèles d’hébergement de services entièrement managés pour les conteneurs et les ordinateurs virtuels. Lorsque vous utilisez des services Azure entièrement gérés, vos applications peuvent tirer parti de l’évolutivité, de la haute disponibilité et de la sécurité intégrée à Azure.

- **Utilisation de services Cloud à partir d’applications-** Les applications existantes peuvent incorporer des services Azure pour étendre leurs fonctionnalités.  Cela peut inclure l’ajout de la fonctionnalité de recherche en texte intégral avec [azure recherche cognitive](/azure/search/search-what-is-azure-search), le stockage sécurisé des secrets d’application dans [Azure Key Vault](/azure/key-vault/) ou l’ajout de fonctionnalités de vision, de reconnaissance vocale et de prise en charge linguistique avec [Azure cognitive services](/azure/cognitive-services/).  Ces services sont entièrement gérés par Azure et peuvent être facilement ajoutés à votre application sans modifier l’architecture de votre application ou le modèle de déploiement actuel.

- **Architectures sans serveur modernes :** Azure Functions simplifier la création de solutions pour gérer les flux de travail pilotés par les événements, qu’il réponde aux requêtes HTTP, gère les chargements de fichiers dans le stockage d’objets BLOB ou traite les événements dans une file d’attente.  Vous écrivez uniquement le code nécessaire pour gérer votre événement sans vous soucier du code des serveurs ou du Framework.  En outre, vous pouvez tirer parti de plus de 250 connecteurs vers d’autres services Azure et tiers pour aborder vos problèmes d’intégration les plus complexes.

## <a name="access-azure-services-from-net-applications"></a>Accéder aux services Azure à partir d’applications .NET

Si votre application est hébergée dans Azure ou localement, l’accès à la plupart des services Azure est assuré via le **Kit de développement logiciel (SDK) Azure pour .net**.  Le kit de développement logiciel (SDK) Azure pour .NET est fourni sous la forme d’une série de packages NuGet qui peuvent être utilisés dans les applications .NET Core (2,1 et ultérieures) et .NET Framework (4.6.1 et versions ultérieures). Le kit de développement logiciel (SDK) Azure pour .NET facilite l’intégration des services Azure dans votre application, tout comme l’installation du package NuGet approprié, l’instanciation d’un objet client et l’appel des méthodes appropriées. Pour plus d’informations sur le kit de développement logiciel (SDK) Azure pour .NET, consultez la [Présentation du kit de développement logiciel (SDK) Azure pour .net](./sdk/azure-sdk-for-dotnet.md).

![Diagramme montrant comment les applications .NET utilisent le kit de développement logiciel (SDK) Azure pour accéder aux services Azure](./media/azure-sdk-for-dotnet-overview.png)

## <a name="next-steps"></a>Étapes suivantes

Découvrez ensuite les [services Azure les plus couramment utilisés](./key-azure-services.md) pour le développement .net.
