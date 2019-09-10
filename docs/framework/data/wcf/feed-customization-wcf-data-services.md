---
title: Personnalisation des flux (services de données WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
ms.openlocfilehash: 17d54210d7abc16fe91fa94f39a8f85eac866088
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854188"
---
# <a name="feed-customization-wcf-data-services"></a>Personnalisation des flux (services de données WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]utilise le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pour exposer des données sous forme de flux. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]prend en charge les formats Atom et JavaScript Object Notation (JSON) pour les flux de données. Lorsque vous utilisez un flux Atom, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fournit une méthode standard pour sérialiser les données, telles que les entités et les relations, dans un format XML qui peut être inclus dans le corps du message http. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]définit un mappage de propriété d’entité par défaut entre les données contenues dans les entités et les éléments Atom. Pour plus d’informations, [consultez OData : Format](https://go.microsoft.com/fwlink/?LinkID=185794)Atom.  
  
 Vous pouvez avoir un scénario d'application qui requiert que les données de propriété retournées par le service des données soient sérialisées de façon personnalisée plutôt qu'au format de flux standard. Avec [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], vous pouvez personnaliser la sérialisation dans un flux de données afin que les propriétés d’une entité puissent être mappées aux éléments inutilisés et aux attributs d’une entrée ou à des éléments personnalisés d’une entrée dans le flux.  
  
> [!NOTE]
> La personnalisation de flux est prise en charge uniquement pour les flux Atom. Les flux personnalisés ne sont pas retournés lorsque le format JSON est demandé pour le flux retourné.  
  
 Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez définir un autre mappage de propriété pour les charges utiles Atom en appliquant manuellement des attributs aux types d'entité dans le modèle de données. Le fournisseur de sources de données du service de données détermine le mode d'application de ces attributs.  
  
> [!IMPORTANT]
> Lorsque vous définissez des flux personnalisés, vous devez vérifier que toutes les propriétés de l'entité qui ont des mappages personnalisés définis sont incluses dans la projection. Lorsqu'une propriété d'entité mappée n'est pas incluse dans la projection, une perte de données peut se produire. Pour plus d’informations, consultez [projections de requête](query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Personnalisation de flux avec le fournisseur Entity Framework  
 Le modèle de données utilisé avec le fournisseur Entity Framework est représenté sous la forme de code XML dans le fichier .edmx. Dans ce cas, les attributs qui définissent des flux personnalisés sont ajoutés aux éléments `EntityType` et `Property` qui représentent des types et des propriétés d'entité dans le modèle de données. Ces attributs de personnalisation de flux ne sont pas [définis dans \[MC\]-CSDL : Le format de fichier](https://go.microsoft.com/fwlink/?LinkId=159072)de définition de schéma conceptuel, qui est le format que le fournisseur de Entity Framework utilise pour définir le modèle de données. Par conséquent, vous devez déclarer les attributs de personnalisation de flux dans un espace de noms de schéma spécifique défini sous la forme `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Le fragment XML suivant affiche des attributs de personnalisation de flux appliqués aux éléments `Property` du type d'entité `Products` qui définissent les propriétés `ProductName`, `ReorderLevel` et `UnitsInStock`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Ces attributs produisent le flux de données personnalisé suivant pour le jeu d'entités `Products`. Dans le flux de données personnalisé, la valeur de la propriété `ProductName` s'affiche à la fois dans l'élément `author` et comme élément de propriété `ProductName`, et la propriété `UnitsInStock` s'affiche dans un élément personnalisé possédant son propre espace de noms unique et avec la propriété `ReorderLevel` comme attribut :  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Pour plus d'informations, voir [Procédure : Personnaliser les flux avec le fournisseur](how-to-customize-feeds-with-ef-provider-wcf-data-services.md)Entity Framework.  
  
> [!NOTE]
> Étant donné que les extensions au modèle de données ne sont pas prises en charge par le Concepteur d'entités, vous devez modifier manuellement le fichier XML qui contient le modèle de données. Pour plus d’informations sur le fichier. edmx généré par les outils de Entity Data Model, consultez [vue d’ensemble du fichier. edmx (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).  
  
### <a name="custom-feed-attributes"></a>Attributs de flux personnalisés  
 La table suivante affiche les attributs XML qui personnalisent les flux que vous pouvez ajouter au CSDL (Conceptual Schema Definition Language) qui définit le modèle de données. Ces attributs sont équivalents aux propriétés de <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> utilisées avec le fournisseur de réflexion.  
  
|Nom d'attribut|Description|  
|--------------------|-----------------|  
|`FC_ContentKind`|Indique le type de contenu. Les mots clés suivants définissent des types de contenu de syndication.<br /><br /> `text:`La valeur de la propriété est affichée dans le flux sous forme de texte.<br /><br /> `html:`La valeur de la propriété est affichée dans le flux au format HTML.<br /><br /> `xhtml:`La valeur de la propriété est affichée dans le flux en tant que code HTML au format XML.<br /><br /> Ces mots clés sont équivalents aux valeurs de l'énumération <xref:System.Data.Services.Common.SyndicationTextContentKind> utilisées avec le fournisseur de réflexion.<br /><br /> Cet attribut n'est pas pris en charge lorsque les attributs `FC_NsPrefix` et `FC_NsUri` sont utilisés.<br /><br /> Lorsque vous spécifiez une valeur de `xhtml` pour l'attribut `FC_ContentKind`, vous devez vérifier que la valeur de propriété contient le formatage XML approprié. Le service de données retourne la valeur sans effectuer de transformations. Vous devez également vérifier que tous les préfixes d'élément XML dans le XML retourné ont un URI d'espace de noms et le préfixe défini dans le flux mappé.|  
|`FC_KeepInContent`|Indique que la valeur de propriété référencée doit être incluse à la fois dans la section de contenu du flux et dans l'emplacement mappé. Les valeurs valides sont `true` et `false`. Pour rendre le flux résultant à compatibilité descendante avec les versions [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]antérieures de, spécifiez `true` la valeur pour vous assurer que la valeur est incluse dans la section de contenu du flux.|  
|`FC_NsPrefix`|Préfixe d'espace de noms de l'élément XML dans un mappage de non-syndication. Cet attribut doit être utilisé avec l'attribut `FC_NsUri` et ne peut pas être utilisé avec l'attribut `FC_ContentKind`.|  
|`FC_NsUri`|URI d'espace de noms de l'élément XML dans un mappage de non-syndication. Cet attribut doit être utilisé avec l'attribut `FC_NsPrefix` et ne peut pas être utilisé avec l'attribut `FC_ContentKind`.|  
|`FC_SourcePath`|Chemin d'accès de la propriété de l'entité à laquelle s'applique cette règle de mappage de flux. Cet attribut est pris en charge uniquement lorsqu'il est utilisé dans un élément `EntityType`.<br /><br /> La propriété <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> ne peut pas référencer directement de type complexe. Pour les types complexes, vous devez utiliser une expression de chemin d’accès où les noms de propriété sont séparés par une barre oblique inverse (`/`). Par exemple, les valeurs suivantes sont autorisées pour un type `Person` d’entité avec une propriété `Age` d’entier et une propriété complexe<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> La propriété <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> ne peut pas avoir une valeur qui contient un espace ou un autre caractère qui n'est pas valide dans un nom de propriété.|  
|`FC_TargetPath`|Nom de l'élément cible du flux résultant pour mapper la propriété. Cet élément peut être un élément défini par la spécification Atom ou un élément personnalisé.<br /><br /> Les mots clés suivants sont des valeurs cible-chemin d’accès de syndication prédéfinies qui pointent vers un emplacement spécifique dans un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].<br /><br /> `SyndicationAuthorEmail:`Élément enfant de l' `atom:author`élément. `atom:email`<br /><br /> `SyndicationAuthorName:`Élément enfant de l' `atom:author`élément. `atom:name`<br /><br /> `SyndicationAuthorUri:`Élément enfant de l' `atom:author`élément. `atom:uri`<br /><br /> `SyndicationContributorEmail:`Élément enfant de l' `atom:contributor`élément. `atom:email`<br /><br /> `SyndicationContributorName:`Élément enfant de l' `atom:contributor`élément. `atom:name`<br /><br /> `SyndicationContributorUri:`Élément enfant de l' `atom:contributor`élément. `atom:uri`<br /><br /> `SyndicationCustomProperty:`Élément de propriété personnalisé. Lors du mappage à un élément personnalisé, la cible doit être une expression de chemin d’accès où les éléments imbriqués sont séparés par une barre oblique inverse (`/`) et les attributs sont spécifiés par une esperluette (`@`). Dans l'exemple suivant, la chaîne `UnitsInStock/@ReorderLevel` mappe une valeur de propriété à un attribut nommé `ReorderLevel` sur un élément enfant nommé `UnitsInStock` de l'élément d'entrée racine.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Lorsque la cible est un nom d'élément personnalisé, les attributs `FC_NsPrefix` et `FC_NsUri` doivent également être spécifiés.<br /><br /> `SyndicationPublished:``atom:published` Élément.<br /><br /> `SyndicationRights:``atom:rights` Élément.<br /><br /> `SyndicationSummary:``atom:summary` Élément.<br /><br /> `SyndicationTitle:``atom:title` Élément.<br /><br /> `SyndicationUpdated:``atom:updated` Élément.<br /><br /> Ces mots clés sont équivalents aux valeurs de l'énumération <xref:System.Data.Services.Common.SyndicationItemProperty> utilisées avec le fournisseur de réflexion.|  
  
> [!NOTE]
> Les noms et valeurs d'attributs respectent la casse. Les attributs peuvent être appliqués à l'élément `EntityType` ou à un ou plusieurs éléments `Property`, mais pas aux deux.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Personnalisation des flux avec le fournisseur de réflexion  
 Pour personnaliser des flux pour un modèle de données ayant été implémenté à l'aide du fournisseur de réflexion, ajoutez une ou plusieurs instances de l'attribut <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> aux classes qui représentent des types d'entité dans le modèle de données. Les propriétés de la classe <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> correspondent aux attributs de personnalisation du flux décrits dans la section précédente. Voici un exemple de la déclaration du type `Order` avec le mappage de flux personnalisé défini pour les deux propriétés.  
  
> [!NOTE]
> Le modèle de données de cet exemple est défini dans la [rubrique Procédure : Créez un service de données à l’aide](create-a-data-service-using-rp-wcf-data-services.md)du fournisseur de réflexion.  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Ces attributs produisent le flux de données personnalisé suivant pour le jeu d'entités `Orders`. Dans ce flux personnalisé, la `OrderId` valeur de propriété s’affiche uniquement `title` dans l’élément `entry` de et `Customer` la valeur de propriété s’affiche `author` à la fois dans `Customer` l’élément et en tant qu’élément de propriété :  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Pour plus d’informations, consultez [Guide pratique pour Personnaliser les flux avec le fournisseur](how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md)de réflexion.  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Personnalisation de flux avec un fournisseur de services de données personnalisé  
 La personnalisation de flux pour un modèle de données défini à l'aide d'un fournisseur de services de données personnalisé est définie pour un type de ressource en appelant le <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> sur l'objet <xref:System.Data.Services.Providers.ResourceType> qui représente un type d'entité dans le modèle de données. Pour plus d’informations, consultez [fournisseurs de services de données personnalisés](custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Consommation de flux personnalisés  
 Lorsque votre application consomme directement un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux, elle doit pouvoir traiter les éléments et les attributs personnalisés dans le flux retourné. Lorsque vous avez implémenté des flux personnalisés dans votre modèle de données, indépendamment du fournisseur de services de données, le point de terminaison `$metadata` retourne des informations de flux personnalisées sous la forme d'attributs de flux personnalisés dans le CSDL retourné par le service de données. Lorsque vous utilisez la boîte de dialogue **Ajouter une référence de service** ou l’outil [outil DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) pour générer des classes de service de données client, les attributs de flux personnalisés sont utilisés pour garantir que les demandes et les réponses au service de données sont gérées correctement.  
  
## <a name="feed-customization-considerations"></a>Considérations de personnalisation de flux  
 Tenez compte des considérations suivantes lorsque vous définissez des mappages de flux personnalisés.  
  
- Le [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client traite les éléments mappés dans un flux comme vides lorsqu’ils contiennent uniquement des espaces blancs. Pour cette raison, les éléments mappés qui contiennent uniquement des espaces blancs ne sont pas matérialisés sur le client avec le même espace blanc. Pour conserver cet espace blanc sur le client, vous devez définir la valeur de `KeepInContext` sur `true` dans l’attribut de mappage de flux.  
  
## <a name="versioning-requirements"></a>Exigences pour le contrôle de version  
 La personnalisation de flux a les conditions requises pour le contrôle de version de protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] suivantes :  
  
- La personnalisation de flux requiert que le client et le service de données prennent en charge les versions 2.0 et ultérieures du protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .  
  
 Pour plus d’informations, consultez contrôle de [version des services de données](data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseur de réflexion](reflection-provider-wcf-data-services.md)
- [Fournisseur Entity Framework](entity-framework-provider-wcf-data-services.md)
