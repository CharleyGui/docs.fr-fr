---
title: Contrôle de version d'un service de données (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 283d3a0a0350823be8c0680dd24e04999b040363
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641132"
---
# <a name="data-service-versioning-wcf-data-services"></a>Contrôle de version d'un service de données (WCF Data Services)
Le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] vous permet de créer des services de données afin que les clients peuvent accéder aux données en tant que ressources à l’aide d’URI qui sont basés sur un modèle de données. OData prend également en charge la définition des opérations de service. Après leur déploiement initial, et potentiellement plusieurs fois pendant leur durée de vie, il peut s’avérer nécessaire de modifier ces services de données pour diverses raisons, telles que l’évolution des besoins de l’entreprise, des exigences informatiques, ou pour résoudre d’autres problèmes. Lorsque vous apportez des modifications à un service de données existant, vous devez choisir de définir une nouvelle version de votre service de données et comment mieux réduire l'impact sur les applications clientes existantes. Cette rubrique fournit des conseils sur le moment et la façon de créer une nouvelle version d'un service de données. Elle décrit également comment WCF Data Services gère l’échange entre les clients et les services de données qui prennent en charge différentes versions du protocole OData.

## <a name="versioning-a-wcf-data-service"></a>Contrôle de version d'un service de données WCF
 Lorsqu'un service de données est déployé et que les données sont en cours de consommation, le service de données peut provoquer des problèmes de compatibilité avec les applications clientes existantes. Toutefois, étant donné que les modifications sont souvent requises par les exigences opérationnelles globales du service, vous devez déterminer quand et comment créer une nouvelle version de votre service de données avec le moins d'impact possible sur les applications clientes.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Modifications du modèle de données qui recommandent une nouvelle version de service de données
 Au moment de choisir de publier ou non une nouvelle version d'un service de données, il est important de comprendre comment les différents types de modifications peuvent affecter les applications clientes. Les modifications apportées à un service de données pouvant nécessiter la création d'une nouvelle version de service de données, appartiennent aux deux catégories suivantes :

- Modifications apportées au contrat de service, incluant les mises à jour des opérations de service, les modifications de l'accessibilité des jeux d'entités (flux), les modifications de version et d'autres modifications apportées aux comportements de service.

- Modifications apportées au contrat de données, incluant les modifications apportées au modèle de données, aux formats de flux ou aux personnalisations de flux.

 Le tableau suivant contient les types de modifications pour lesquelles vous devez envisager de publier une nouvelle version du service de données :

|Type de modification|Requiert une nouvelle version|Nouvelle version inutile|
|--------------------|----------------------------|----------------------------|
|Opérations de service|-Ajouter un nouveau paramètre<br />-Modifier le type de retour<br />-Opération de suppression de service|-Supprimer un paramètre existant<br />-Ajouter une nouvelle opération de service|
|Comportements de service|-Désactiver les demandes de nombre<br />-Désactivez la prise en charge de projection<br />-Augmentation de la version de service de données requises|-Autoriser les demandes de nombre<br />-Activer la prise en charge de projection<br />-Réduire la version de service de données requises|
|Autorisations du jeu d'entités|-Limiter les autorisations du jeu d’entités<br />-Modifier le code de réponse (nouvelle première valeur de chiffres) <sup>1</sup>|-Assouplir les autorisations du jeu d’entités<br />-Modifier le code de réponse (même première valeur de chiffres)|
|Propriétés d'entité|-Supprimer de la propriété ou relation existante<br />-Ajouter une propriété non nullable<br />-Modifier la propriété existante|-Ajouter une propriété nullable<sup>2</sup>|
|Jeux d'entités|-Supprimer le jeu d’entités|-Ajouter un type dérivé<br />-Modifier le type de base<br />-Ajouter le jeu d’entités|
|Personnalisation de flux|-Modifier le mappage de propriété d’entité||

 <sup>1</sup> cela peut dépendre de la rigueur avec laquelle une application cliente s’appuie sur la réception d’un code d’erreur spécifique.

 <sup>2</sup> vous pouvez définir le <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> propriété `true` pour que le client ignore les nouvelles propriétés envoyées par le service de données qui ne sont pas définies sur le client. Toutefois, lorsque des insertions sont réalisées, les propriétés non incluses par le client dans la demande POST sont définies sur leurs valeurs par défaut. Pour les mises à jour, toutes les données existantes dans une propriété inconnue du client peuvent être remplacées par les valeurs par défaut. Dans ce cas, vous devez envoyer la mise à jour sous la forme d’une demande MERGE, qui est la valeur par défaut. Pour plus d’informations, consultez [gérer le contexte de Service de données](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Procédure de versionnage d'un service de données
 Si nécessaire, une nouvelle version de service de données est définie en créant une nouvelle instance du service avec un contrat de service ou un modèle de données mis à jour. Ce nouveau service est alors exposé à l'aide d'un nouveau point de terminaison d'URI, qui le distingue de la version antérieure. Exemple :

- Ancienne version : `http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nouvelle version : `http://services.odata.org/Northwind/v2/Northwind.svc/`

 Lors de la mise à niveau d'un service de données, les clients doivent également être mis à jour en fonction des nouvelles métadonnées de service de données et utiliser le nouveau URI racine. Si possible, vous devez maintenir la version antérieure du service de données pour prendre en charge les clients qui n'ont pas encore été mis à niveau pour utiliser la nouvelle version. Les versions antérieures d'un service de données peuvent être supprimées lorsqu'elles sont devenues inutiles. Vous devez envisager de conserver l'URI de point de terminaison de service de données dans un fichier de configuration externe.

## <a name="odata-protocol-versions"></a>Versions du protocole OData
 Comme les nouvelles versions d’OData sont publiées, les applications clientes ne peuvent pas être à l’aide de la même version du protocole OData est pris en charge par le service de données. Une ancienne application cliente peut accéder à un service de données qui prend en charge une version plus récente d’OData. Une application cliente peut également utiliser une version plus récente de la bibliothèque cliente WCF Data Services, qui prend en charge une version plus récente d’OData que ne le service de données qui est accédé.

 WCF Data Services s’appuie sur la prise en charge par OData pour gérer de tels scénarios de contrôle de version. Il est également prise en charge de la génération et l’utilisation des métadonnées de modèle de données pour créer des classes de service de données client lorsque le client utilise une version différente d’OData que les données de service utilise. Pour plus d’informations, consultez [OData : Le contrôle de version de protocole](https://go.microsoft.com/fwlink/?LinkId=186071).

### <a name="version-negotiation"></a>Négociation de version
 Le service de données peut être configuré pour définir la version la plus récente du protocole OData qui sera utilisé par le service, quelle que soit la version demandée par le client. Vous pouvez le faire en spécifiant un <xref:System.Data.Services.Common.DataServiceProtocolVersion> valeur pour le <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> propriété de la <xref:System.Data.Services.DataServiceBehavior> utilisé par le service de données. Pour plus d’informations, consultez [configuration du Service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

 Lorsqu’une application utilise les bibliothèques de client WCF Data Services pour accéder à un service de données, les bibliothèques définir automatiquement ces en-têtes avec les valeurs appropriées, selon la version de OData et les fonctionnalités qui sont utilisées dans votre application. Par défaut, WCF Data Services utilise la plus ancienne version de protocole qui prend en charge l’opération demandée.

 Le tableau suivant répertorie les versions de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] et [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] qui incluent la prise en charge de WCF Data Services pour des versions spécifiques du protocole OData.

|Version du protocole OData|Prise en charge depuis...|
|-----------------------------------------------------------------------------------|----------------------------|
|Version 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] version 3|
|Version 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-Une mise à jour [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1. Vous pouvez télécharger et installer la mise à jour à partir de la [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=158125).<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] version 4|
|Version 3|-Vous pouvez télécharger et installer une version préliminaire qui prend en charge OData version 3 à partir de la [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=203885).|

### <a name="metadata-versions"></a>Versions de métadonnées
 Par défaut, WCF Data Services utilise la version 1.1 de CSDL pour représenter un modèle de données. C'est toujours le cas pour les modèles de données basés sur un fournisseur de réflexion ou un fournisseur de services de données personnalisé. Toutefois, lorsque le modèle de données est défini à l'aide d'[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)], la version de CSDL retournée est la même que celle utilisée par l'[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. La version du langage CSDL est déterminée par l’espace de noms de la [Schema, élément (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl).

 L'élément `DataServices` des métadonnées retournées contient également un attribut `DataServiceVersion`, qui est la même valeur que l'en-tête `DataServiceVersion` du message de réponse. Les applications clientes, telles que la **ajouter une référence de Service** boîte de dialogue dans Visual Studio, utilisez ces informations pour générer des classes de service de données client qui fonctionnent correctement avec la version de WCF Data Services qui hébergent le service de données. Pour plus d’informations, consultez [OData : Le contrôle de version de protocole](https://go.microsoft.com/fwlink/?LinkId=186071).

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
