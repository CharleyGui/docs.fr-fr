---
title: Génération des exemples Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: ee1c8101e31464fa203341d53137525433782c18
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253831"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Génération des exemples Windows Communication Foundation

Les exemples Windows Communication Foundation (WCF) peuvent être générés à l’aide de l’IDE Visual Studio ou à l’aide de la commande **MSBuild** à partir de la ligne de commande. Les deux procédures sont décrites dans cette rubrique.

> [!NOTE]
> Avant de générer ou d’exécuter l’un des exemples WCF, assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

## <a name="to-build-the-sample-using-a-command-prompt"></a>Pour générer l'exemple à partir d'une invite de commandes

1. Ouvrez Invite de commandes développeur pour Visual Studio et accédez au sous-répertoire spécifique à la langue sous l’emplacement du répertoire où vous avez installé l’exemple.

2. Tapez `msbuild` sur la ligne de commande. Les fichiers programme du client sont générés sur *Client\Bin* et les fichiers programme du service sont générés sur *service\bin*. Si le service est hébergé par Internet Information Services (IIS), les fichiers programme du service sont également copiés dans le répertoire *servicemodelsamples* et dans son sous-répertoire *\Bin* .

> [!NOTE]
> Vous devez définir les listes de contrôle d’accès sur *répertoire%systemdrive%\Inetpub\Wwwroot.* pour accorder des autorisations de modification au compte sous lequel vous exécutez. Sinon, certains des événements post-build échoueront. Vous pouvez également laisser les listes de contrôle d'accès telles quelles et exécuter l'invite de commandes du Kit de développement logiciel (SDK) en tant qu'administrateur.

## <a name="to-build-the-sample-using-visual-studio"></a>Pour générer l'exemple à l'aide de Visual Studio

1. Dans le menu **fichier** de Visual Studio, sélectionnez **ouvrir** un  >  **projet/une solution**. Accédez au sous-répertoire spécifique au langage sous le répertoire dans lequel vous avez installé l’exemple, puis double-cliquez sur l’icône du fichier. sln pour ouvrir la solution dans Visual Studio.

1. Dans le menu **générer** , sélectionnez **régénérer la solution**.

   Les fichiers de programme du client sont générés dans client\bin, et les fichiers de programme du service sont générés dans service\bin. Si le service est hébergé dans IIS, les fichiers programme du service sont également copiés dans le répertoire *servicemodelsamples* et dans son sous-répertoire *\Bin* .

> [!NOTE]
> Vous devez affecter %systemdrive%\inetpub\wwwroot aux listes de contrôle d'accès (ACL) pour accorder des autorisations de modification au compte sous lequel vous vous êtes connecté. Sinon, certains des événements post-build échoueront. Vous pouvez également laisser les listes de contrôle d'accès telles quelles et exécuter l'invite de commandes du Kit de développement logiciel (SDK) ou Visual Studio en tant qu'administrateur. Certaines actions Visual Studio (telles que l’attachement d’un débogueur au processus de travail ASP.NET) requièrent également des privilèges d’administrateur.

## <a name="setup-batch-files-and-scripts"></a>Scripts et fichiers de commandes d'installation

 Setup.exe et les scripts Cleanup.exe et les fichiers de commandes doivent être exécutés à partir de Invite de commandes développeur pour Visual Studio. Plusieurs fichiers d'installation et de nettoyage effectuent des tâches qui requièrent des privilèges d'administrateur et doivent être lancés avec des privilèges d'administrateur.

## <a name="important-security-information-about-metadata-endpoints"></a>Informations de sécurité importantes à propos des points de terminaison de métadonnées

 Pour empêcher la divulgation non intentionnelle de métadonnées de service potentiellement sensibles, la configuration par défaut pour les services Windows Communication Foundation (WCF) désactive la publication de métadonnées. Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration. Pour faciliter l'utilisation des exemples, pratiquement tous les exemples exposent un point de terminaison de publication de métadonnées non sécurisé. De tels points de terminaison sont potentiellement disponibles aux consommateurs non authentifiés anonymes et il est nécessaire de se montrer vigilant et de s'assurer que la divulgation publique des métadonnées d'un service est appropriée avant de déployer de tels points de terminaison. Pour plus d’informations sur la publication de métadonnées de service, consultez l’exemple de [comportement de publication des métadonnées](metadata-publishing-behavior.md) . Consultez l’exemple de [point de terminaison de métadonnées sécurisées personnalisé](custom-secure-metadata-endpoint.md) pour obtenir un exemple de sécurisation d’un point de terminaison.

## <a name="exception-handling"></a>Gestion des exceptions

 En général, ces exemples n'incluent pas la gestion des exceptions pour que le code reste axé sur le sujet de l'exemple. Pour plus d’informations sur la gestion des exceptions, consultez l’exemple [exceptions attendues](expected-exceptions.md) .

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Régénération des clients et de la configuration avec Svcutil

 Vous pouvez utiliser l' [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour régénérer le code client et la configuration pour la plupart des exemples. Certains exemples nécessitent une modification manuelle de la configuration. Par exemple, si vous utilisez Svcutil.exe pour régénérer la configuration d'un exemple qui utilise des informations d'identification de certificat client, vous devez spécifier manuellement les informations d'identification précédemment configurées. Certains exemples utilisent des options Svcutil.exe spécifiques pour affecter le code généré ; ces options sont spécifiées dans les rubriques d'exemple spécifiques.

### <a name="to-regenerate-the-client-and-configuration-files"></a>Pour régénérer les fichiers du client et les fichiers de configuration

1. Ouvrez une invite de commandes du Kit de développement SDK et accédez au sous-répertoire spécifique aux langues situé sous l'emplacement d'installation de l'exemple.

2. Si le service est un type hébergé sur le Web, utilisez la commande suivante.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Si le service est un type auto-hébergé, utilisez la commande suivante.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Remplacez `http://localhost:8000/ServiceModelSamples/service.svc/mex` par l’adresse du point de terminaison MEX du service auto-hébergé.

     Pour générer le client dans un type Visual Basic, utilisez la commande suivante.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     Si le service est un type auto-hébergé, utilisez la commande suivante.

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > Pour ignorer la génération de la configuration du client, ajoutez l’option **/noconfig** .

## <a name="see-also"></a>Voir aussi

- [Exécution des exemples Windows Communication Foundation](running-the-samples.md)
- [Outil Service Model Metadata Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
