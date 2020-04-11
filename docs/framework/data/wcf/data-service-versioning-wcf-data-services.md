---
title: Contrôle de version d'un service de données (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: f82ab4c98e724bbed658a6c77de9c5a5d5c3390f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121536"
---
# <a name="data-service-versioning-wcf-data-services"></a>Contrôle de version d'un service de données (WCF Data Services)
Le protocole de données ouvertes (OData) vous permet de créer des services de données afin que les clients puissent accéder aux données en tant que ressources utilisant des URL basées sur un modèle de données. OData prend également en charge la définition des opérations de service. Après leur déploiement initial, et potentiellement plusieurs fois pendant leur durée de vie, il peut s’avérer nécessaire de modifier ces services de données pour diverses raisons, telles que l’évolution des besoins de l’entreprise, des exigences informatiques, ou pour résoudre d’autres problèmes. Lorsque vous apportez des modifications à un service de données existant, vous devez choisir de définir une nouvelle version de votre service de données et comment mieux réduire l'impact sur les applications clientes existantes. Cette rubrique fournit des conseils sur le moment et la façon de créer une nouvelle version d'un service de données. Il décrit également comment WCF Data Services gère un échange entre les clients et les services de données qui prennent en charge différentes versions du protocole OData.

## <a name="versioning-a-wcf-data-service"></a>Contrôle de version d'un service de données WCF
 Lorsqu'un service de données est déployé et que les données sont en cours de consommation, le service de données peut provoquer des problèmes de compatibilité avec les applications clientes existantes. Toutefois, étant donné que les modifications sont souvent requises par les exigences opérationnelles globales du service, vous devez déterminer quand et comment créer une nouvelle version de votre service de données avec le moins d'impact possible sur les applications clientes.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Modifications du modèle de données qui recommandent une nouvelle version de service de données
 Au moment de choisir de publier ou non une nouvelle version d'un service de données, il est important de comprendre comment les différents types de modifications peuvent affecter les applications clientes. Les modifications apportées à un service de données pouvant nécessiter la création d'une nouvelle version de service de données, appartiennent aux deux catégories suivantes :

- Modifications apportées au contrat de service, incluant les mises à jour des opérations de service, les modifications de l'accessibilité des jeux d'entités (flux), les modifications de version et d'autres modifications apportées aux comportements de service.

- Modifications apportées au contrat de données, incluant les modifications apportées au modèle de données, aux formats de flux ou aux personnalisations de flux.

 Le tableau suivant contient les types de modifications pour lesquelles vous devez envisager de publier une nouvelle version du service de données :

|Type de modification|Requiert une nouvelle version|Nouvelle version inutile|
|--------------------|----------------------------|----------------------------|
|Opérations de service|- Ajouter un nouveau paramètre<br />- Changement de type de retour<br />- Supprimer l’opération de service|- Supprimer le paramètre existant<br />- Ajouter une nouvelle opération de service|
|Comportements de service|- Désactiver les demandes de comptage<br />- Soutien à la projection de désactivation<br />- Augmenter la version de service de données requise|- Activer les demandes de comptage<br />- Activer le support de projection<br />- Diminuer la version de service de données requise|
|Autorisations du jeu d'entités|- Restreindre les autorisations d’ensemble d’entités<br />- Code de réponse de modification (nouvelle valeur de premier chiffre) <sup>1</sup>|- Détendez les autorisations d’entité<br />- Modifier le code de réponse (même valeur de premier chiffre)|
|Propriétés d'entité|- Supprimer les biens ou relations existants<br />- Ajouter des biens non annulables<br />- Changer la propriété existante|- Ajouter la propriété annulée<sup>2</sup>|
|Jeux d'entités|- Supprimer l’ensemble d’entités|- Ajouter le type dérivé<br />- Changement de type de base<br />- Ajouter l’ensemble d’entités|
|Personnalisation de flux|- Modifier la cartographie entité-propriété||

 <sup>1</sup> Cela peut dépendre de la façon dont une application client repose strictement sur la réception d’un code d’erreur spécifique.

 <sup>2</sup> Vous pouvez <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> définir `true` la propriété pour que le client ignore toutes les nouvelles propriétés envoyées par le service de données qui ne sont pas définis sur le client. Toutefois, lorsque des insertions sont réalisées, les propriétés non incluses par le client dans la demande POST sont définies sur leurs valeurs par défaut. Pour les mises à jour, toutes les données existantes dans une propriété inconnue du client peuvent être remplacées par les valeurs par défaut. Dans ce cas, vous devez envoyer la mise à jour sous la forme d’une demande MERGE, qui est la valeur par défaut. Pour plus d’informations, voir [Gérer le contexte du service de données](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Procédure de versionnage d'un service de données
 Si nécessaire, une nouvelle version de service de données est définie en créant une nouvelle instance du service avec un contrat de service ou un modèle de données mis à jour. Ce nouveau service est alors exposé à l'aide d'un nouveau point de terminaison d'URI, qui le distingue de la version antérieure. Par exemple :

- Ancienne version : `http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nouvelle version : `http://services.odata.org/Northwind/v2/Northwind.svc/`

 Lors de la mise à niveau d'un service de données, les clients doivent également être mis à jour en fonction des nouvelles métadonnées de service de données et utiliser le nouveau URI racine. Si possible, vous devez maintenir la version antérieure du service de données pour prendre en charge les clients qui n'ont pas encore été mis à niveau pour utiliser la nouvelle version. Les versions antérieures d'un service de données peuvent être supprimées lorsqu'elles sont devenues inutiles. Vous devez envisager de conserver l'URI de point de terminaison de service de données dans un fichier de configuration externe.

## <a name="odata-protocol-versions"></a>Versions du protocole OData
 Au fur et à mesure que les nouvelles versions d’OData sont publiées, les applications client peuvent ne pas utiliser la même version du protocole OData qui est pris en charge par le service de données. Une ancienne application client peut accéder à un service de données qui prend en charge une version plus récente d’OData. Une application client peut également utiliser une version plus récente de la bibliothèque client WCF Data Services, qui prend en charge une version plus récente d’OData que le service de données qui est accessible.

 WCF Data Services tire parti du soutien fourni par OData pour gérer ces scénarios de version. Il existe également un support pour la génération et l’utilisation de métadonnées de modèle de données pour créer des classes de service de données des clients lorsque le client utilise une version différente d’OData que le service de données utilise. Pour plus d’informations, consultez la section Version du protocole dans l’article [OData: Overview.](https://www.odata.org/documentation/odata-version-2-0/overview/)

### <a name="version-negotiation"></a>Négociation de version
 Le service de données peut être configuré pour définir la version la plus élevée du protocole OData qui sera utilisée par le service, quelle que soit la version demandée par le client. Vous pouvez le faire <xref:System.Data.Services.Common.DataServiceProtocolVersion> en spécifiant une valeur pour la <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> propriété de l’utilisé <xref:System.Data.Services.DataServiceBehavior> par le service de données. Pour plus d’informations, voir [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).

 Lorsqu’une application utilise les bibliothèques clients de WCF Data Services pour accéder à un service de données, les bibliothèques fixent automatiquement ces en-têtes aux valeurs correctes, selon la version d’OData et les fonctionnalités utilisées dans votre application. Par défaut, WCF Data Services utilise la version de protocole la plus basse qui prend en charge l’opération demandée.

 Le tableau suivant détaille les versions de .NET Framework et Silverlight qui incluent le support WCF Data Services pour des versions spécifiques du protocole OData.

|Version protocole OData|Prise en charge depuis...|
|-----------------------------------------------------------------------------------|----------------------------|
|version 1|- .NET Framework 3.5 Service Pack 1 (SP1)<br />- Version Silverlight 3|
|version 2|- .NET Cadre 4<br />- Version Silverlight 4|

### <a name="metadata-versions"></a>Versions de métadonnées
 Par défaut, WCF Data Services utilise la version 1.1 de CSDL pour représenter un modèle de données. C'est toujours le cas pour les modèles de données basés sur un fournisseur de réflexion ou un fournisseur de services de données personnalisé. Toutefois, lorsque le modèle de données est défini à l'aide d'Entity Framework, la version de CSDL retournée est la même que celle utilisée par Entity Framework. La version de la CSDL est déterminée par le nomspace de [l’élément Schema (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl).

 L'élément `DataServices` des métadonnées retournées contient également un attribut `DataServiceVersion`, qui est la même valeur que l'en-tête `DataServiceVersion` du message de réponse. Les applications client, telles que la boîte de dialogue **Add Service Reference** dans Visual Studio, utilisent ces informations pour générer des classes de service de données client qui fonctionnent correctement avec la version de WCF Data Services qui héberge le service de données. Pour plus d’informations, consultez la section Version du protocole dans l’article [OData: Overview.](https://www.odata.org/documentation/odata-version-2-0/overview/)

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de services de données](data-services-providers-wcf-data-services.md)
- [Définition des services de données WCF](defining-wcf-data-services.md)
