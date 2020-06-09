---
title: Service Debug Behavior
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 53f21129860c644d09d1a2eb9cb956aecf8ab0ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596637"
---
# <a name="service-debug-behavior"></a>Service Debug Behavior

Cet exemple montre comment configurer les paramètres de comportement de débogage de service. L’exemple est basé sur le [prise en main](getting-started-sample.md), qui implémente le `ICalculator` contrat de service. Cet exemple définit explicitement le comportement de débogage de service dans le fichier de configuration. Cela peut également être fait de façon impérative dans le code.

Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Le fichier Web.config du serveur définit le comportement de débogage de service permettant d'activer la page d'aide et la gestion des exceptions, tel qu'indiqué dans l'exemple suivant.

```xml
<behaviors>
     <serviceBehaviors>
         <behavior name="CalculatorServiceBehavior">
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->
         <!-- Please set this to false when deploying -->
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>
         </behavior>
     </serviceBehaviors>
</behaviors>
```

[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)est l’élément de configuration qui permet de modifier les propriétés de comportement de débogage de service. L'utilisateur peut modifier ce comportement aux fins suivantes :

- Cela permet au service de retourner une exceptions levée par le code d'application même si celle-ci n'est pas déclarée à l'aide de <xref:System.ServiceModel.FaultContractAttribute>. Pour ce faire, affectez `includeExceptionDetailInFaults` à `true`. Ce paramètre est utile lors du débogage de cas où le serveur lève une exception inattendue.

  > [!IMPORTANT]
  > Pour des raisons de sécurité, il est déconseillé d'activer ce paramètre dans un environnement de production. Une exception de serveur inattendue peut contenir des informations qui ne sont pas destinées au client et l'affectation de `includeExceptionDetailsInFaults` à `true` peut entraîner une fuite des informations.

- [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)Permet également à un utilisateur d’activer ou de désactiver la page d’aide. Chaque service peut éventuellement exposer une page d'aide qui contient des informations sur le service, et notamment le point de terminaison permettant d'obtenir le WSDL pour le service. Pour ce faire, affectez `httpHelpPageEnabled` à `true`. Cela permet de retourner la page d'aide dans une demande GET à l'adresse de base du service. Pour modifier cette adresse, définissez un autre attribut `httpHelpPageUrl`. Pour sécuriser cette procédure, utilisez HTTPS au lieu de HTTP. Pour ce faire, définissez `httpsHelpPageEnabled` et `httpsHelpPageUrl`

Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Les trois premières opérations (ajout, soustraction et multiplication) doivent réussir. La dernière (division) échoue avec une exception de division par zéro.

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
