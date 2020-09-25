---
title: Contrôle de version d'un service de données (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 8d7cc0f0033c75c05ac9c39cfbf1ce09dc032a4c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91182868"
---
# <a name="data-service-versioning-wcf-data-services"></a>Contrôle de version d'un service de données (WCF Data Services)

Le Open Data Protocol (OData) vous permet de créer des services de données afin que les clients puissent accéder aux données en tant que ressources à l’aide d’URI basés sur un modèle de données. OData prend également en charge la définition d’opérations de service. Après leur déploiement initial, et potentiellement plusieurs fois pendant leur durée de vie, il peut s’avérer nécessaire de modifier ces services de données pour diverses raisons, telles que l’évolution des besoins de l’entreprise, des exigences informatiques, ou pour résoudre d’autres problèmes. Lorsque vous apportez des modifications à un service de données existant, vous devez choisir de définir une nouvelle version de votre service de données et comment mieux réduire l'impact sur les applications clientes existantes. Cette rubrique fournit des conseils sur le moment et la façon de créer une nouvelle version d'un service de données. Elle explique également comment WCF Data Services gère un échange entre les clients et les services de données qui prennent en charge différentes versions du protocole OData.

## <a name="versioning-a-wcf-data-service"></a>Contrôle de version d'un service de données WCF

 Lorsqu'un service de données est déployé et que les données sont en cours de consommation, le service de données peut provoquer des problèmes de compatibilité avec les applications clientes existantes. Toutefois, étant donné que les modifications sont souvent requises par les exigences opérationnelles globales du service, vous devez déterminer quand et comment créer une nouvelle version de votre service de données avec le moins d'impact possible sur les applications clientes.

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>Modifications du modèle de données qui recommandent une nouvelle version de service de données

 Au moment de choisir de publier ou non une nouvelle version d'un service de données, il est important de comprendre comment les différents types de modifications peuvent affecter les applications clientes. Les modifications apportées à un service de données pouvant nécessiter la création d'une nouvelle version de service de données, appartiennent aux deux catégories suivantes :

- Modifications apportées au contrat de service, incluant les mises à jour des opérations de service, les modifications de l'accessibilité des jeux d'entités (flux), les modifications de version et d'autres modifications apportées aux comportements de service.

- Modifications apportées au contrat de données, incluant les modifications apportées au modèle de données, aux formats de flux ou aux personnalisations de flux.

 Le tableau suivant contient les types de modifications pour lesquelles vous devez envisager de publier une nouvelle version du service de données :

|Type de modification|Requiert une nouvelle version|Nouvelle version inutile|
|--------------------|----------------------------|----------------------------|
|Opérations de service|-Ajouter un nouveau paramètre<br />-Modifier le type de retour<br />-Supprimer l’opération de service|-Supprimer un paramètre existant<br />-Ajouter une nouvelle opération de service|
|Comportements de service|-Désactiver les demandes de nombre<br />-Désactiver la prise en charge de la projection<br />-Augmenter la version du service de données requis|-Activer les demandes de nombre<br />-Activer la prise en charge de la projection<br />-Diminuer la version du service de données requise|
|Autorisations du jeu d'entités|-Restreindre les autorisations du jeu d’entités<br />-Modifier le code de réponse (nouvelle valeur du premier chiffre) <sup>1</sup>|-Assouplir les autorisations du jeu d’entités<br />-Modifier le code de réponse (même première valeur de chiffre)|
|Propriétés d'entité|-Supprimer la propriété ou la relation existante<br />-Ajouter une propriété qui n’accepte pas les valeurs null<br />-Modifier la propriété existante|-Ajouter la propriété Nullable<sup>2</sup>|
|Jeux d'entités|-Supprimer le jeu d’entités|-Ajouter un type dérivé<br />-Modifier le type de base<br />-Ajouter un jeu d’entités|
|Personnalisation de flux|-Modifier le mappage d’entité-propriété||

 <sup>1</sup> cela peut dépendre de la façon dont une application cliente s’appuie sur la réception d’un code d’erreur spécifique.

 <sup>2</sup> vous pouvez affecter à la propriété la valeur <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> `true` pour que le client ignore toutes les nouvelles propriétés envoyées par le service de données qui ne sont pas définies sur le client. Toutefois, lorsque des insertions sont réalisées, les propriétés non incluses par le client dans la demande POST sont définies sur leurs valeurs par défaut. Pour les mises à jour, toutes les données existantes dans une propriété inconnue du client peuvent être remplacées par les valeurs par défaut. Dans ce cas, vous devez envoyer la mise à jour sous la forme d’une demande MERGE, qui est la valeur par défaut. Pour plus d’informations, consultez [gestion du contexte du service de données](managing-the-data-service-context-wcf-data-services.md).

### <a name="how-to-version-a-data-service"></a>Procédure de versionnage d'un service de données

 Si nécessaire, une nouvelle version de service de données est définie en créant une nouvelle instance du service avec un contrat de service ou un modèle de données mis à jour. Ce nouveau service est alors exposé à l'aide d'un nouveau point de terminaison d'URI, qui le distingue de la version antérieure. Par exemple :

- Ancienne version : `http://services.odata.org/Northwind/v1/Northwind.svc/`

- Nouvelle version : `http://services.odata.org/Northwind/v2/Northwind.svc/`

 Lors de la mise à niveau d'un service de données, les clients doivent également être mis à jour en fonction des nouvelles métadonnées de service de données et utiliser le nouveau URI racine. Si possible, vous devez maintenir la version antérieure du service de données pour prendre en charge les clients qui n'ont pas encore été mis à niveau pour utiliser la nouvelle version. Les versions antérieures d'un service de données peuvent être supprimées lorsqu'elles sont devenues inutiles. Vous devez envisager de conserver l'URI de point de terminaison de service de données dans un fichier de configuration externe.

## <a name="odata-protocol-versions"></a>Versions du protocole OData

 À mesure que de nouvelles versions d’OData sont publiées, les applications clientes peuvent ne pas utiliser la même version du protocole OData prise en charge par le service de données. Une application cliente plus ancienne peut accéder à un service de données qui prend en charge une version plus récente d’OData. Une application cliente peut également utiliser une version plus récente de la bibliothèque cliente WCF Data Services, qui prend en charge une version plus récente d’OData que le service de données qui fait l’objet d’un accès.

 WCF Data Services tire parti de la prise en charge fournie par OData pour gérer de tels scénarios de contrôle de version. Il existe également une prise en charge de la génération et de l’utilisation des métadonnées du modèle de données pour créer des classes de service de données client lorsque le client utilise une autre version d’OData que celle utilisée par le service de données. Pour plus d’informations, consultez la section Protocol Versioning dans l’article [OData : Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) .

### <a name="version-negotiation"></a>Négociation de version

 Le service de données peut être configuré pour définir la version la plus récente du protocole OData qui sera utilisée par le service, quelle que soit la version demandée par le client. Pour ce faire, vous pouvez spécifier une <xref:System.Data.Services.Common.DataServiceProtocolVersion> valeur pour la <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> propriété du <xref:System.Data.Services.DataServiceBehavior> utilisé par le service de données. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md).

 Lorsqu’une application utilise les bibliothèques clientes WCF Data Services pour accéder à un service de données, les bibliothèques définissent automatiquement ces en-têtes sur les valeurs correctes, en fonction de la version d’OData et des fonctionnalités utilisées dans votre application. Par défaut, WCF Data Services utilise la version de protocole la plus basse qui prend en charge l’opération demandée.

 Le tableau suivant détaille les versions de .NET Framework et Silverlight qui incluent la prise en charge WCF Data Services pour des versions spécifiques du protocole OData.

|Version du protocole OData|Prise en charge depuis...|
|-----------------------------------------------------------------------------------|----------------------------|
|version 1|-.NET Framework 3,5 Service Pack 1 (SP1)<br />-Silverlight version 3|
|version 2|-.NET Framework 4<br />-Silverlight version 4|

### <a name="metadata-versions"></a>Versions de métadonnées

 Par défaut, WCF Data Services utilise la version 1,1 de CSDL pour représenter un modèle de données. C'est toujours le cas pour les modèles de données basés sur un fournisseur de réflexion ou un fournisseur de services de données personnalisé. Toutefois, lorsque le modèle de données est défini à l'aide d'Entity Framework, la version de CSDL retournée est la même que celle utilisée par Entity Framework. La version du langage CSDL est déterminée par l’espace de noms de l' [élément de schéma (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl).

 L'élément `DataServices` des métadonnées retournées contient également un attribut `DataServiceVersion`, qui est la même valeur que l'en-tête `DataServiceVersion` du message de réponse. Les applications clientes, telles que la boîte de dialogue **Ajouter une référence de service** dans Visual Studio, utilisent ces informations pour générer des classes de service de données client qui fonctionnent correctement avec la version de WCF Data Services qui hébergent le service de données. Pour plus d’informations, consultez la section Protocol Versioning dans l’article [OData : Overview](https://www.odata.org/documentation/odata-version-2-0/overview/) .

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de services de données](data-services-providers-wcf-data-services.md)
- [Définition des services de données WCF](defining-wcf-data-services.md)
