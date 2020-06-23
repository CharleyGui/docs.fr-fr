---
title: 'Didacticiel : créer un client Windows Communication Foundation'
description: Apprenez à créer un client en extrayant les métadonnées d’un service WCF dans le cadre d’une série d’articles qui vous aideront à créer une application WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246322"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Didacticiel : créer un client Windows Communication Foundation

Ce didacticiel décrit la quatrième des cinq tâches nécessaires à la création d’une application de base Windows Communication Foundation (WCF). Pour obtenir une vue d’ensemble des didacticiels, consultez [Didacticiel : prise en main des applications Windows Communication Foundation](getting-started-tutorial.md).

La tâche suivante pour créer une application WCF consiste à créer un client en extrayant les métadonnées d’un service WCF. Vous utilisez Visual Studio pour ajouter une référence de service, qui obtient les métadonnées du point de terminaison MEX du service. Visual Studio génère ensuite un fichier de code source managé pour un proxy client dans le langage que vous avez choisi. Il crée également un fichier de configuration client (*App.config*). Ce fichier permet à l’application cliente de se connecter au service au niveau d’un point de terminaison.

> [!NOTE]
> Si vous appelez un service WCF à partir d’un projet de bibliothèque de classes dans Visual Studio, utilisez la fonctionnalité **Ajouter une référence de service** pour générer automatiquement un proxy et un fichier de configuration associé. Toutefois, étant donné que les projets de bibliothèque de classes n’utilisent pas ce fichier de configuration, vous devez ajouter les paramètres dans le fichier de configuration généré au fichier *App.config* pour l’exécutable qui appelle la bibliothèque de classes.

> [!NOTE]
> Vous pouvez également utiliser l' [outil ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) au lieu de Visual Studio pour générer la classe proxy et le fichier de configuration.

L'application cliente utilise la classe proxy générée pour communiquer avec le service. Cette procédure est décrite dans [Didacticiel : utiliser un client](how-to-use-a-wcf-client.md).

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Créez et configurez un projet d’application console pour le client WCF.
> - Ajoutez une référence de service au service WCF pour générer la classe proxy et les fichiers de configuration.

## <a name="create-a-windows-communication-foundation-client"></a>Créer un client Windows Communication Foundation

1. Créez un projet d’application console dans Visual Studio :

    1. Dans le menu **fichier** , sélectionnez **ouvrir**  >  un**projet/une solution** , puis accédez à la solution **gettingstarted** que vous avez créée précédemment (*gettingstarted. sln*). Sélectionnez **Ouvrir**.

    2. Dans le menu **affichage** , sélectionnez **Explorateur de solutions**.

    3. Dans la fenêtre **Explorateur de solutions** , sélectionnez la solution **gettingstarted** (nœud supérieur), puis sélectionnez **Ajouter**  >  **un nouveau projet** dans le menu contextuel.

    4. Dans la fenêtre **Ajouter un nouveau projet** , sur le côté gauche, sélectionnez la catégorie **Bureau Windows** sous **Visual C#** ou **Visual Basic**.

    5. Sélectionnez le modèle **application console (.NET Framework)** , puis entrez *GettingStartedClient* pour le **nom**. Sélectionnez **OK**.

2. Ajoutez une référence dans le projet **GettingStartedClient** à l' <xref:System.ServiceModel> assembly :

    1. Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedClient** , puis sélectionnez Ajouter une **référence** dans le menu contextuel.

    2. Dans la fenêtre **Ajouter une référence** , sous **assemblys** sur le côté gauche de la fenêtre, sélectionnez **Framework**.

    3. Recherchez et sélectionnez **System. ServiceModel**, puis choisissez **OK**.

    4. Enregistrez la solution en sélectionnant **fichier**  >  **enregistrer tout**.

3. Ajoutez une référence de service au service de calculatrice :

   1. Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedClient** , puis sélectionnez **Ajouter une référence de service** dans le menu contextuel.

   2. Dans la fenêtre **Ajouter une référence de service** , sélectionnez **découvrir**.

      Le service CalculatorService démarre et Visual Studio l’affiche dans la zone **services** .

   3. Sélectionnez **CalculatorService** pour le développer et afficher les contrats de service implémentés par le service. Laissez l' **espace de noms** par défaut et choisissez **OK**.

      Visual Studio ajoute un nouvel élément sous le dossier **services connectés** dans le projet **GettingStartedClient** .

### <a name="servicemodel-metadata-utility-tool"></a>Outil utilitaire de métadonnées ServiceModel

Les exemples suivants montrent comment utiliser l' [outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le fichier de classe proxy. Cet outil génère le fichier de classe proxy et le fichier *App.config* . Les exemples suivants montrent comment générer le proxy en C# et Visual Basic, respectivement :

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Fichier de configuration du client

Une fois le client créé, Visual Studio crée le **App.config** fichier de configuration dans le projet **GettingStartedClient** , qui doit ressembler à l’exemple suivant :

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

Sous la [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notez l' [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) élément. L’élément de ** &lt; point de terminaison &gt; ** définit le point de terminaison que le client utilise pour accéder au service comme suit :

- Adresse : `http://localhost:8000/GettingStarted/CalculatorService` . Adresse du point de terminaison.
- Contrat de service : `ServiceReference1.ICalculator` . Le contrat de service gère la communication entre le client WCF et le service. Visual Studio a généré ce contrat lorsque vous avez utilisé sa fonction **Ajouter une référence de service** . Il s’agit essentiellement d’une copie du contrat que vous avez défini dans le projet GettingStartedLib.
- Liaison : <xref:System.ServiceModel.WSHttpBinding> . La liaison spécifie HTTP comme transport, la sécurité interopérable et d’autres détails de configuration.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Créez et configurez un projet d’application console pour le client WCF.
> - Ajoutez une référence de service au service WCF pour générer la classe proxy et les fichiers de configuration pour l’application cliente.

Passez au didacticiel suivant pour découvrir comment utiliser le client généré.

> [!div class="nextstepaction"]
> [Didacticiel : utiliser un client WCF](how-to-use-a-wcf-client.md)
