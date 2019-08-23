---
title: Activation basée sur la configuration dans les services IIS et WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: f4de4aff2fbe6b8e82dc3d6523f492d06494c79e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909768"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Activation basée sur la configuration dans les services IIS et WAS

Normalement, lors de l’hébergement d’un service Windows Communication Foundation (WCF) sous Internet Information Services (IIS) ou WAS (Windows Process Activation Service), vous devez fournir un fichier. svc. Le fichier .svc contient le nom du service et une fabrique hôte de service personnalisée facultative. Ce fichier supplémentaire facilite encore la gestion. Grâce à la fonctionnalité d’activation basée sur la configuration, le fichier .svc et, par conséquent, les surcharges associées ne sont plus indispensables.

## <a name="configuration-based-activation"></a>Activation basée sur la configuration

L'activation basée sur la configuration prend les métadonnées qui étaient placées dans le fichier .svc et les met dans le fichier Web.config. Dans l’élément`serviceHostingEnvironment`< > il existe un élément`serviceActivations`< >. Dans le <`serviceActivations`> élément est un ou plusieurs éléments`add`< >, un pour chaque service hébergé. L’élément`add`< > contient des attributs qui vous permettent de définir l’adresse relative du service et le type de service ou une fabrique d’hôte de service. L'exemple de code de configuration suivant montre comment cette section est utilisée.

> [!NOTE]
> Chaque <`add`élément > doit spécifier un service ou un attribut Factory. Il est possible de spécifier les deux.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 Grâce à ce code dans le fichier Web.config, vous pouvez placer le code source du service dans le répertoire App_Code de l'application ou un assembly compilé dans le répertoire Bin de l'application.

> [!NOTE]
> - Lors d'une activation basée sur la configuration, le code inline dans les fichiers .svc n'est pas pris en charge.
> - L' `relativeAddress` attribut doit être défini sur une adresse relative telle que «\<sous-répertoire >/service.svc» ou «~/\<Sub-Directory/Service. svc».
> - Une exception de configuration est levée si vous inscrivez une adresse relative sans extension connue, associée à WCF.
> - L'adresse relative spécifiée est relative à la racine de l'application virtuelle.
> - En raison du modèle hiérarchique de configuration, les adresses relatives enregistrées au niveau de l'ordinateur et du site sont héritées par les applications virtuelles.
> - Les inscriptions dans un fichier de configuration sont prioritaires sur les paramètres d'un fichier .svc, .xamlx, .xoml ou autre.
> - Toute '\' (barre oblique inverse) qui se trouve dans un URI envoyé aux services IIS/WAS est automatiquement convertie en '/' (barre oblique). Si une adresse relative contenant un signe '\' est ajoutée et que vous envoyez à IIS un URI utilisant cette adresse relative, la barre oblique inverse est convertie en barre oblique et IIS ne peut pas le faire correspondre à l'adresse relative. IIS envoie des informations de suivi qui indiquent qu'aucune correspondance n'a été trouvée.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Hébergement de services](../../../../docs/framework/wcf/hosting-services.md)
- [Vue d’ensemble de l’hébergement de services de workflow](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201276)
