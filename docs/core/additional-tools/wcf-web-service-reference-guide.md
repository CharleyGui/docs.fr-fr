---
title: Ajouter WCF Web Service Reference
description: Vue d’ensemble de l’outil Microsoft WCF Web Service Reference Provider, qui ajoute des fonctionnalités pour les projets .NET Core et ASP.NET Core, de manière similaire à la fonctionnalité Ajouter une référence de service pour les projets .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: cdd6b457d289dd7b752c97c5645f0797f24b72aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715684"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>Utiliser l’outil WCF Web Service Reference Provider

Au fil des années, de nombreux développeurs Visual Studio ont apprécié le gain de productivité offert par l’outil [**Ajouter une référence de service**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) quand leurs projets .NET Framework avaient besoin d’accéder à des services web.  L’outil **WCF Web Service Reference** est une extension de service connecté de Visual Studio qui fournit une expérience semblable à la fonctionnalité Ajouter une référence de service pour les projets .NET Core et ASP.NET Core. Cet outil récupère les métadonnées d’un service web dans la solution actuelle sur un emplacement réseau ou dans un fichier WSDL, puis génère un fichier source compatible .NET Core contenant du code de proxy client WCF (Windows Communication Foundation) que vous pouvez utiliser pour accéder au service web.

> [!IMPORTANT]
> Vous devez référencer des services uniquement à partir d’une source approuvée. L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.

## <a name="prerequisites"></a>Conditions préalables requises

- [Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ou versions ultérieures

## <a name="how-to-use-the-extension"></a>Comment utiliser l’extension

> [!NOTE]
> L’option **WCF Web Service Reference** s’applique aux projets créés à l’aide des modèles de projet suivants :
>
> - **Coeur visuel** > **.NET**
> - **Norme visuelle CMD** > **.NET**
> - **Application** > Web de**cœur** de la**ASP.NET Web** > Visual CMD

Prenant le modèle de projet **Application web ASP.NET Core** en guise d’exemple, cet article explique comment ajouter une référence de service WCF au projet :

1. Dans l’Explorateur de solutions, double-cliquez sur le nœud du projet **Services connectés** (pour un projet .NET Core ou .NET Standard, cette option est disponible quand vous cliquez avec le bouton droit sur le nœud **Dépendances** du projet dans l’Explorateur de solutions).

    La page **Services connectés** s’affiche, comme illustré ci-dessous :

    ![Onglet Services connectés de Visual Studio pour .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Dans la page **Services connectés**, cliquez sur **Microsoft WCF Web Service Reference Provider**. L’Assistant **Configurer la référence de services web WCF** apparaît :

    ![Onglet Point de terminaison de service Visual Studio pour .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Sélectionnez un service.

    3a. Plusieurs options de recherche de services sont disponibles dans l’Assistant **Configurer la référence de services web WCF** :

     * Pour rechercher parmi les services définis dans la solution actuelle, cliquez sur le bouton **Découvrir**.
     * Pour rechercher parmi les services hébergés à une adresse spécifiée, entrez une URL de service dans la zone **Adresse**, puis cliquez sur le bouton **Envoyer**.
     * Pour sélectionner un fichier WSDL qui contient les informations de métadonnées de service web, cliquez sur le bouton **Parcourir**.

    3b. Sélectionnez le service dans la liste des résultats de recherche dans la zone **Services**. Si nécessaire, entrez l’espace de noms du code généré dans la zone de texte **Espace de noms** correspondante.

    3c. Cliquez sur le bouton **Suivant** pour ouvrir les pages **Options du type de données** et **Options du client**. Vous pouvez aussi cliquer sur le bouton **Terminer** pour utiliser les options par défaut.

4. Le formulaire **Options du type de données** vous permet d’affiner les paramètres de configuration de référence de service générés :

    ![Onglet Options du type de données Visual Studio pour .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > La case à cocher **Réutiliser les types dans les assemblys référencés** est utile quand les types de données nécessaires pour la génération du code de référence de service sont définis dans l’un des assemblys référencés de votre projet.  Il est important de réutiliser ces types de données existants pour éviter les conflits de type au moment de la compilation ou les problèmes au moment de l’exécution.

    Il peut y avoir un délai pendant le chargement des informations de type, en fonction du nombre de dépendances du projet et d’autres facteurs de performances système. Le bouton **Terminer** est désactivé pendant le chargement, sauf si la case **Réutiliser les types dans les assemblys référencés** est cochée.

5. Cliquez sur **Terminer** quand vous avez terminé.

Lors de l’affichage de la progression, l’outil :

- Télécharge les métadonnées à partir du service WCF.
- Génère le code de référence de service dans un fichier nommé *reference.cs* et l’ajoute à votre projet sous le nœud **Services connectés**.
- Met à jour le fichier projet (.csproj) avec les références de package NuGet nécessaires pour la compilation et l’exécution sur la plateforme cible.

![Fenêtre de progression Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Une fois ces processus terminés, vous pouvez créer une instance du type de client WCF généré et appeler les opérations de service.

## <a name="see-also"></a>Voir aussi

- [Lancez-vous avec les applications de la Fondation Windows Communication](../../framework/wcf/getting-started-tutorial.md)
- [Services de la Fondation Windows Communication et services de données WCF dans Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [WCF caractéristiques prises en charge sur .NET Core](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a>Commentaires et questions

Si vous avez des questions ou des commentaires, signalez-les à [Developer Community](https://developercommunity.visualstudio.com/) à l’aide du [Rapport d’un](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) outil à problème.

## <a name="release-notes"></a>Notes de publication

- Pour obtenir des informations à jour sur les versions, notamment les problèmes connus, consultez les [Notes de publication](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md).
