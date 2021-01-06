---
title: Présentation du kit de développement logiciel (SDK) Azure pour .NET
description: Fournit une vue d’ensemble du kit de développement logiciel (SDK) Azure pour .NET et des étapes de base pour utiliser le kit de développement logiciel (SDK) dans une application .NET
ms.date: 11/30/2020
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 3ec1ee9e8da3a6e03581ce2a29a655ec0d68fe54
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701118"
---
# <a name="azure-sdk-for-net-overview"></a>Présentation du kit de développement logiciel (SDK) Azure pour .NET

## <a name="what-is-the-azure-sdk-for-net"></a>Présentation du kit de développement logiciel (SDK) Azure pour .NET

Le **Kit de développement logiciel (SDK) Azure pour .net** est conçu pour faciliter l’utilisation des services Azure à partir de vos applications .net.  Qu’il s’agisse de charger et de télécharger des fichiers vers le stockage d’objets BLOB, de récupérer des secrets d’application Azure Key Vault ou de traiter des notifications à partir d’Azure Event Hubs, le kit de développement logiciel (SDK) Azure pour .NET fournit une interface cohérente et familière pour accéder aux services Azure.  

Le kit de développement logiciel (SDK) Azure pour .NET est disponible sous la forme d’une série de packages NuGet qui peuvent être utilisés dans les applications .NET Core (2,1 et ultérieures) et .NET Framework (4.6.1 et versions ultérieures).

![Diagramme montrant comment les applications .NET utilisent le kit de développement logiciel (SDK) Azure pour accéder aux services Azure](./media/azure-sdk-for-dotnet-overview.png)

## <a name="use-the-azure-sdk-for-net-in-your-applications"></a>Utiliser le kit de développement logiciel (SDK) Azure pour .NET dans vos applications

Pour utiliser un package du kit de développement logiciel (SDK) Azure dans l’une de vos applications .NET, vous devez suivre les étapes ci-dessous.

1. **Recherchez le package du kit de développement logiciel (SDK) approprié :** Utilisez la [liste package](../packages.md) pour rechercher le package approprié pour le service Azure que vous utilisez.  Il est recommandé que la plupart des services disposent d’un package client pour l’utilisation du service et d’un package de gestion pour créer et gérer des instances du service.  Dans la plupart des cas, vous souhaiterez le package client.  Installez ce package dans votre application à l’aide de NuGet.

2. **Configurer l’authentification pour votre application-** Pour accéder aux ressources Azure, votre application doit disposer des informations d’identification et des droits d’accès appropriés affectés dans Azure.  Découvrez comment configurer l’authentification [pour authentifier des applications .net dans Azure](../authentication.md).

3. **Écrire du code à l’aide du kit de développement logiciel (SDK) dans votre application** Lorsque vous utilisez des services Azure, votre code crée d’abord un objet client pour travailler avec le service, puis appelle des méthodes sur cet objet client pour interagir avec le service.  Des méthodes synchrones et asynchrones sont fournies.  Vous trouverez des exemples d’utilisation de chaque package du kit de développement logiciel (SDK) dans tout le contenu de la documentation Azure.

4. **Configurer la journalisation pour le kit de développement logiciel (facultatif)-** Si vous avez besoin de diagnostiquer des problèmes entre votre application et Azure, vous pouvez [activer la journalisation dans le kit de développement logiciel (SDK) Azure pour .net](./logging.md).
