---
title: 'Tutorial: Créer un client Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184099"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Tutorial: Créer un client Windows Communication Foundation

Ce tutoriel décrit la quatrième des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF). Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).

La prochaine tâche pour créer une application WCF est de créer un client en récupérant des métadonnées à partir d’un service WCF. Vous utilisez Visual Studio pour ajouter une référence de service, qui obtient les métadonnées à partir du point de terminaison MEX du service. Visual Studio génère ensuite un fichier de code source géré pour un proxy client dans la langue que vous avez choisie. Il crée également un fichier de configuration client (*App.config*). Ce fichier permet à l’application client de se connecter au service à un point de terminaison.

> [!NOTE]
> Si vous appelez un service WCF à partir d’un projet de bibliothèque de classe dans Visual Studio, utilisez la fonction **Add Service Reference** pour générer automatiquement un fichier de configuration proxy et associé. Toutefois, comme les projets de bibliothèque de classe n’utilisent pas ce fichier de configuration, vous devez ajouter les paramètres du fichier de configuration généré au fichier *App.config* pour l’exécutable qui appelle la bibliothèque de classe.

> [!NOTE]
> Comme alternative, utilisez [l’outil ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) au lieu de Visual Studio pour générer la classe proxy et le fichier de configuration.

L'application cliente utilise la classe proxy générée pour communiquer avec le service. Cette procédure est décrite dans [Tutorial: Utilisez un client](how-to-use-a-wcf-client.md).

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Créez et configurez un projet d’application console pour le client WCF.
> - Ajoutez une référence de service au service WCF pour générer la classe proxy et les fichiers de configuration.

## <a name="create-a-windows-communication-foundation-client"></a>Créer un client de la Fondation Windows Communication

1. Créez un projet d’application console dans Visual Studio :

    1. Du menu **Fichier,** sélectionnez **Open** > **Project/Solution** et naviguez vers la solution **GettingStarted** que vous avez déjà créée (*GettingStarted.sln*). Sélectionnez **uvrir**.

    2. Du menu **View,** sélectionnez **Solution Explorer**.

    3. Dans la fenêtre **Solution Explorer,** sélectionnez la solution **GettingStarted** (nœud supérieur), puis **sélectionnez Ajouter** > **un nouveau projet** dans le menu raccourci.

    4. Dans la fenêtre **Add New Project,** sur le côté gauche, sélectionnez la catégorie **Windows Desktop** sous Visual **C ou** **Visual Basic**.

    5. Sélectionnez le modèle **Console App (.NET Framework)** et *entrez GettingStartedClient* pour le **nom**. Sélectionnez **OK**.

2. Ajoutez une référence dans le projet **GettingStartedClient** à l’assemblage <xref:System.ServiceModel> :

    1. Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **Références** dans le cadre du projet **GettingStartedClient,** puis **sélectionnez Ajouter la référence** dans le menu raccourci.

    2. Dans la fenêtre **Add Reference,** sous **les assemblées** sur le côté gauche de la fenêtre, sélectionnez **Cadre**.

    3. Trouver et sélectionner **System.ServiceModel**, puis choisissez **OK**.

    4. Enregistrer la solution en sélectionnant **File** > **Save All**.

3. Ajouter une référence de service au service de calculatrice :

   1. Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **Références** dans le cadre du projet **GettingStartedClient,** puis **sélectionnez Ajouter** la référence de service dans le menu raccourci.

   2. Dans la fenêtre **Add Service Reference,** sélectionnez **Discover**.

      Le service CalculatorService démarre et Visual Studio l’affiche dans la boîte **services.**

   3. Sélectionnez **CalculatorService** pour l’élargir et afficher les contrats de service mis en œuvre par le service. Laissez **l’espace nom** par défaut et choisissez **OK**.

      Visual Studio ajoute un nouvel article sous le dossier **Services connectés** dans le projet **GettingStartedClient.**

### <a name="servicemodel-metadata-utility-tool"></a>Outil utilitaire De métadonnées de service

Les exemples suivants montrent comment utiliser en option [l’outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le fichier de classe proxy. Cet outil génère le fichier de classe proxy et le fichier *App.config.* Les exemples suivants montrent comment générer le proxy dans C et Visual Basic, respectivement:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Fichier de configuration du client

Après avoir créé le client, Visual Studio crée le fichier de configuration **App.config** dans le projet **GettingStartedClient,** qui doit être similaire à l’exemple suivant :

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

Dans la [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) [ \<section system.serviceModel>,](../configure-apps/file-schema/wcf/system-servicemodel.md) remarquez le critère de>élément. ** &lt;L’élément&gt; de point de terminaison** définit le critère d’évaluation que le client utilise pour accéder au service comme suit :

- Adresse: `http://localhost:8000/GettingStarted/CalculatorService`. Adresse du point de terminaison.
- Contrat de `ServiceReference1.ICalculator`service: . Le contrat de service traite de la communication entre le client WCF et le service. Visual Studio a généré ce contrat lorsque vous avez utilisé sa fonction **Add Service Reference.** Il s’agit essentiellement d’une copie du contrat que vous avez défini dans le projet GettingStartedLib.
- Liaison: <xref:System.ServiceModel.WSHttpBinding>. La liaison spécifie HTTP comme le transport, la sécurité interopérable, et d’autres détails de configuration.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Créez et configurez un projet d’application console pour le client WCF.
> - Ajoutez une référence de service au service WCF pour générer la classe de proxy et les fichiers de configuration pour l’application client.

Avancez au tutoriel suivant pour apprendre à utiliser le client généré.

> [!div class="nextstepaction"]
> [Tutorial: Utilisez un client WCF](how-to-use-a-wcf-client.md)
