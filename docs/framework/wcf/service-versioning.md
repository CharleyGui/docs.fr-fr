---
title: Contrôle des versions du service
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: ea5e80e33d1b29e01e6d1867c50bb3bb973b01c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183123"
---
# <a name="service-versioning"></a>Contrôle des versions du service
Après leur déploiement initial, et potentiellement plusieurs fois pendant leur durée de vie, il peut s’avérer nécessaire de modifier les services (et les points de terminaison qu’ils exposent) pour diverses raisons, telles que l’évolution des besoins de l’entreprise, des exigences informatiques, ou pour résoudre d’autres problèmes. Chaque modification introduit une nouvelle version du service. Ce sujet explique comment envisager la version dans Windows Communication Foundation (WCF).  
  
## <a name="four-categories-of-service-changes"></a>Quatre catégories de modifications de service  
 Les modifications apportées aux services qui peuvent s'avérer nécessaires peuvent être classées en quatre catégories :  
  
- Modifications de contrat : par exemple, une opération peut être ajoutée, ou un élément de données dans un message peut être ajouté ou modifié.  
  
- Modifications d'adresse : par exemple, un service se déplace vers un autre emplacement où les points de terminaison ont de nouvelles adresses.  
  
- Modifications de liaison : par exemple, un mécanisme de sécurité change ou ses paramètres changent.  
  
- Modifications d'implémentation : par exemple, lorsqu'une implémentation de méthode interne change.  
  
 Certaines de ces modifications sont dites « avec rupture » et d'autres « sans rupture ». Un changement est *non-démesuré* si tous les messages qui auraient été traités avec succès dans la version précédente sont traités avec succès dans la nouvelle version. Tout changement qui ne répond pas à ce critère est un changement *de rupture.*  
  
## <a name="service-orientation-and-versioning"></a>Contrôle de version et orientation de service  
 L'une des doctrines de l'orientation de service est que les services et les clients sont autonomes (ou indépendants). Cela implique notamment que les développeurs de service ne peuvent pas présumer contrôler, voire même connaître, l'ensemble des clients de service. Cela élimine l'option de régénération et de redéploiement de l'ensemble des clients lorsqu'un service modifie des versions. Cette rubrique suppose que le service adhère à cette doctrine et qu'il doit par conséquent être modifié ou « associé à une version » indépendamment de ses clients.  
  
 Dans les cas où une modification avec rupture est inattendue et ne peut pas être évitée, une application peut choisir d'ignorer cette doctrine et requérir que les clients soient régénérés et redéployés avec une nouvelle version du service.  
  
## <a name="contract-versioning"></a>Contrôle de version des contrats  
 Il n'est pas nécessaire que les contrats utilisés par un client soient les mêmes que celui utilisé par le service ; ils doivent seulement être compatibles.  
  
 Pour les contrats de service, la compatibilité signifie que les nouvelles opérations exposées par le service peuvent être ajoutées, mais que les opérations existantes ne peuvent pas être supprimées ou modifiées sémantiquement.  
  
 Pour les contrats de données, la compatibilité signifie que les nouvelles définitions de type de schéma peuvent être ajoutées, mais que les définitions de type de schéma existantes ne peuvent pas être modifiées avec rupture. Les modifications avec rupture peuvent inclure la suppression de membres de données ou la modification de leur type de données de manière incompatible. Cette fonctionnalité offre une certaine latitude au service pour modifier la version de ses contrats sans interruption des clients. Les deux sections suivantes expliquent les modifications non-rupture et de rupture qui peuvent être apportées aux données et contrats de service de WCF.  
  
## <a name="data-contract-versioning"></a>Contrôle de version des contrats de données  
 Cette section traite du contrôle de version des données lors de l'utilisation des classes <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.DataContractAttribute>.  
  
### <a name="strict-versioning"></a>Contrôle de version strict  
 Dans de nombreux scénarios où la modification des versions pose un problème, le développeur de service n'a pas de contrôle sur les clients et ne peut donc pas faire d'hypothèses quant à la manière dont ils pourraient réagir aux modifications apportées dans le message XML ou le schéma. Dans ce cas, vous devez garantir que les nouveaux messages effectueront une validation par rapport à l'ancien schéma, pour deux raisons :  
  
- Les anciens clients ont été développés dans l'hypothèse que le schéma ne changera pas. Il se peut qu'ils échouent à traiter des messages pour lesquels ils n'ont jamais été conçus.  
  
- Les anciens clients peuvent effectuer la validation de schéma réelle par rapport à l’ancien schéma avant même d’essayer de traiter les messages.  
  
 L'approche recommandée dans les scénarios de ce type consiste à traiter les contrats de données existants comme immuables et à en créer de nouveaux avec des noms complets XML uniques. Le développeur de service dispose alors de deux options : ajouter de nouvelles méthodes à un contrat de service existant ou créer un contrat de service avec des méthodes qui utilisent le nouveau contrat de données.  
  
 Bien souvent, le développeur de service doit écrire la logique métier qui doit s'exécuter dans toutes les versions d'un contrat de données ainsi que le code métier spécifique à la version pour chaque version du contrat de données. L'annexe à la fin de cette rubrique explique comment utiliser les interfaces pour répondre à ce besoin.  
  
### <a name="lax-versioning"></a>Contrôle de version souple  
 Dans de nombreux autres scénarios, le développeur de service peut partir de l'hypothèse que l'ajout d'un nouveau membre facultatif au contrat de données n'interrompra pas les clients existants. Cela implique que le développeur de service étudie si les clients existants n’exécutent pas de validation de schéma et s’ils ignorent des membres de données inconnus. Dans ces scénarios, il est possible de tirer parti des fonctionnalités de contrat de données permettant d'ajouter de nouveaux membres sans rupture. Le développeur de service peut partir sans problème de cette hypothèse si les fonctionnalités de contrat de données permettant le contrôle de version ont déjà été utilisées pour la première version du service.  
  
 WCF, ASP.NET Web Services, et de nombreuses autres piles de services Web prennent en charge *la version laxiste*: c’est-à-dire qu’ils ne jettent pas d’exceptions pour les nouveaux membres inconnus des données reçues.  
  
 On peut facilement croire à tort que l'ajout d'un nouveau membre n'interrompra pas les clients existants. Si vous n'êtes pas certain que tous les clients peuvent gérer le contrôle de version souple, nous vous recommandons de vous conformer aux instructions sur le contrôle de version strict et de traiter les contrats de données comme immuables.  
  
 Pour des lignes directrices détaillées pour la version laxiste et stricte des contrats de données, voir [Meilleures pratiques : Version des contrats de données](best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Distinction entre le contrat de données et les types .NET  
 Une structure ou classe .NET peut être projetée comme contrat de données en appliquant l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à la classe. Le type .NET et ses projections de contrat de données sont deux aspects distincts. Il est possible d'avoir plusieurs types .NET avec la même projection de contrat de données. Cette distinction est particulièrement utile en ce sens qu'elle vous permet de modifier le type .NET tout en conservant le contrat de données projeté, et de conserver ainsi la compatibilité avec les clients existants, et ce même au sens strict du terme. Pour conserver cette distinction entre le type .NET et le contrat de données, vous devez systématiquement effectuer les deux procédures suivantes :  
  
- Spécifiez <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> et <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Vous devez systématiquement spécifier le nom et l'espace de noms de votre contrat de données afin d'empêcher ceux de votre type .NET d'être exposés dans le contrat. De cette façon, si vous décidez ultérieurement de modifier le nom du type ou l'espace de noms .NET, votre contrat de données restera identique.  
  
- Spécifiez <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Vous devez systématiquement spécifier le nom de vos membres de données afin d'empêcher le nom de votre membre .NET d'être exposé dans le contrat. De cette façon, si vous décidez ultérieurement de modifier le nom .NET du membre, votre contrat de données restera identique.  
  
### <a name="changing-or-removing-members"></a>Modification ou suppression de membres  
 La modification du nom ou du type de données d'un membre, ou la suppression des membres de données, est une modification avec rupture si le contrôle de version souple est autorisé. Créez un contrat de données si nécessaire.  
  
 Si la compatibilité de service est importante, vous pouvez envisager d'ignorer les membres de données non utilisés dans votre code et les laisser en place. Si vous fractionnez un membre de données en plusieurs, vous pouvez envisager de laisser le membre existant en place en tant que propriété pouvant exécuter le fractionnement et la réagrégation requis pour les clients de niveau inférieur (clients qui ne sont pas mis à niveau à la dernière version).  
  
 De la même façon, les modifications apportées à l'espace de noms ou au nom du contrat de données sont des modifications avec rupture.  
  
### <a name="round-trips-of-unknown-data"></a>Allers-retours de données inconnues  
 Dans certains scénarios, il est nécessaire d'effectuer un « aller-retour » des données inconnues qui proviennent de membres ajoutées dans une nouvelle version. Par exemple, un service « NouvelleVersion » envoie des données avec des membres récemment ajoutés à un client « AncienneVersion ». Le client ignore les membres récemment ajoutés lors du traitement du message, mais il renvoie ces mêmes données, y compris les membres récemment ajoutés, au service NouvelleVersion. Le scénario classique dans ce cas est la mise à jour des données dans le cadre de laquelle les données sont récupérées à partir du service, modifiées et retournées.  
  
 Pour activer l'aller-retour pour un type spécifique, ce dernier doit implémenter l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject>. L'interface contient la propriété <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> qui retourne le type <xref:System.Runtime.Serialization.ExtensionDataObject>. Cette propriété permet de stocker les données des futures versions du contrat de données qui est inconnu de la version actuelle. Ces données sont opaques pour le client, mais lorsque l'instance est sérialisée, le contenu de la propriété <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> est écrit avec le reste des données des membres de contrat de données.  
  
 Il est recommandé que tous vos types implémentent cette interface afin de prendre en charge les membres nouveaux et inconnus.  
  
### <a name="data-contract-libraries"></a>Bibliothèques de contrats de données  
 Il peut y avoir des bibliothèques de contrats de données dans lesquelles un contrat est publié sur un référentiel central, et des implémenteurs de type et de service qui implémentent et exposent des contrats de données à partir de ce référentiel. Dans ce cas, lorsque vous publiez un contrat de données sur le référentiel, vous n'avez aucun contrôle sur l'élément qui crée les types qui l'implémentent. Par conséquent, vous ne pouvez pas modifier le contrat une fois celui-ci publié, et le rendre ainsi immuable.  
  
### <a name="when-using-the-xmlserializer"></a>Lors de l'utilisation de XmlSerializer  
 Les mêmes principes de contrôle de version s'appliquent lors de l'utilisation de la classe <xref:System.Xml.Serialization.XmlSerializer>. Lorsque le contrôle de version strict est requis, traitez des contrats de données comme immuables et créez des contrats de données avec noms complets uniques pour les nouvelles versions. Si vous êtes certain de pouvoir utiliser le contrôle de version souple, vous pouvez ajouter de nouveaux membres sérialisables dans les nouvelles versions, mais vous ne pouvez pas modifier ou supprimer les membres existants.  
  
> [!NOTE]
> <xref:System.Xml.Serialization.XmlSerializer> utilise les attributs <xref:System.Xml.Serialization.XmlAnyElementAttribute> et <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> pour prendre en charge l'aller-retour des données inconnues.  
  
## <a name="message-contract-versioning"></a>Contrôle de version des contrats de message  
 Les instructions relatives au contrôle de version des contrats de message sont très semblables à celles du contrôle de version des contrats de données. Si le contrôle de version strict est requis, vous ne devez pas modifier le corps de votre message, mais créer à la place un contrat de message avec un nom complet unique. Si vous êtes certain de pouvoir utiliser le contrôle de version souple, vous pouvez ajouter de nouvelles parties de corps de message, mais vous ne pouvez pas modifier ou supprimer des parties existantes. Cette instruction s'applique à la fois aux contrats de message encapsulé et nu.  
  
 Des en-têtes de message peuvent toujours être ajoutés, même si le contrôle de version strict est utilisé. L'indicateur MustUnderstand peut affecter le contrôle de version. En général, le modèle de version des en-têtes dans WCF est tel que décrit dans la spécification SOAP.  
  
## <a name="service-contract-versioning"></a>Contrôle de version des contrats de service  
 À l'instar du contrôle de version des contrats de données, celui concernant les contrats de service implique également des opérations d'ajout, de modification et de suppression.  
  
### <a name="specifying-name-namespace-and-action"></a>Spécification du nom, de l'espace de noms et de l'action  
 Par défaut, le nom d'un contrat de service correspond à celui de l'interface. Son namespace parhttp://tempuri.orgdéfaut est " ",http://tempuri.org/contractname/methodnameet l’action de chaque opération est ". Il est recommandé de spécifier explicitement un nom et un espace dehttp://tempuri.orgnom pour le contrat de service, et une action pour chaque opération afin d’éviter d’utiliser « » et d’empêcher que les noms d’interface et de méthode ne soient exposés dans le contrat du service.  
  
### <a name="adding-parameters-and-operations"></a>Ajout de paramètres et d'opérations  
 L'ajout des opérations de service exposées par le service est une modification sans rupture car les clients existants n'ont pas à se soucier de ces nouvelles opérations.  
  
> [!NOTE]
> L'ajout des opérations à un contrat de rappel duplex est une modification avec rupture.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Modification des types de retours ou de paramètres d'opération  
 La modification des types de retours ou de paramètres est généralement une modification avec rupture, sauf si le nouveau type implémente le même contrat de données implémenté par l'ancien type. Pour apporter une modification de ce type, ajoutez une nouvelle opération au contrat de service ou définissez un nouveau contrat de service.  
  
### <a name="removing-operations"></a>Suppression d'opérations  
 La suppression d'opérations est également une modification avec rupture. Pour apporter une modification de ce type, définissez un nouveau contrat de service et exposez-le sur un nouveau point de terminaison.  
  
### <a name="fault-contracts"></a>Contrats d'erreur  
 L'attribut <xref:System.ServiceModel.FaultContractAttribute> permet à un développeur de contrat de service de spécifier des informations sur les erreurs qui peuvent être retournées par les opérations du contrat.  
  
 La liste d'erreurs décrite dans le contrat d'un service n'est pas considérée comme exhaustive. À tout moment, une opération peut retourner des erreurs qui ne sont pas décrites dans son contrat. Par conséquent, la modification du jeu d'erreurs décrit dans le contrat n'est pas considérée comme une modification avec rupture. Par exemple, ajouter une nouvelle erreur au contrat à l'aide de <xref:System.ServiceModel.FaultContractAttribute> ou supprimer une erreur existante du contrat.  
  
### <a name="service-contract-libraries"></a>Bibliothèques de contrats de service  
 Les entreprises peuvent avoir des bibliothèques de contrats dans lesquelles un contrat est publié sur un référentiel central, et des implémenteurs de service qui implémentent des contrats à partir de ce référentiel. Dans ce cas, lorsque vous publiez un contrat de service sur le référentiel, vous n'avez aucun contrôle sur l'élément qui crée les services qui l'implémentent. Par conséquent, vous ne pouvez pas modifier le contrat de service une fois celui-ci publié, et le rendre ainsi immuable. WCF soutient l’héritage contractuel, qui peut être utilisé pour créer un nouveau contrat qui prolonge les contrats existants. Pour utiliser cette fonctionnalité, définissez une nouvelle interface de contrat de service qui hérite de l'ancienne interface de contrat de service, puis ajoutez-lui des méthodes. Modifiez ensuite le service qui implémente l'ancien contrat pour implémenter le nouveau contrat et modifier la définition de point de terminaison de l'« AncienneVersion » afin d'utiliser le nouveau contrat. Pour les clients de l'« AncienneVersion », le point de terminaison continuera d'exposer le contrat de l'« AncienneVersion » ; pour les clients de la « NouvelleVersion », le point de terminaison exposera le contrat de la « NouvelleVersion ».  
  
## <a name="address-and-binding-versioning"></a>Contrôle de version des adresses et liaisons  
 Les modifications apportées à la liaison et à l'adresse de point de terminaison sont des modifications avec rupture, sauf si les clients sont capables de découvrir dynamiquement la nouvelle liaison ou adresse de point de terminaison. L’un des mécanismes permettant d’implémenter cette fonctionnalité consiste à utiliser un registre UDDI (Universal Discovery Description and Integration) et le modèle d’appel UDDI lorsqu’un client tente de communiquer avec un point de terminaison et, qu’après échec, il interroge un registre UDDI connu pour les métadonnées de point de terminaison actuelles. Le client utilise ensuite l'adresse et la liaison à partir de ces métadonnées pour communiquer avec le point de terminaison. Si cette communication réussit, le client met en cache les informations d'adresse et de liaison pour un usage ultérieur.  
  
## <a name="routing-service-and-versioning"></a>Contrôle de version et service de routage  
 Si les modifications apportées à un service sont des modifications avec rupture et vous n'avez pas besoin de plusieurs versions différentes d'un service exécutées simultanément, vous pouvez utiliser le Service de routage WCF pour acheminer les messages vers l'instance de service appropriée. Le Service de routage WCF utilise le routage basé sur le contenu, c'est-à-dire qu'il utilise les informations contenues dans le message pour déterminer la destination du message. Pour plus d’informations sur le service de routage WCF voir [Service de routage](./feature-details/routing-service.md). Par exemple de la façon d’utiliser le service de routage WCF pour la version de service voir [Comment: Version de service](./feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Annexe  
 Les instructions relatives au contrôle de version des contrats de données lorsque le contrôle de version strict est requis permettent de traiter des contrats de données comme immuables et d'en créer de nouveaux lorsque des modifications sont requises. Une nouvelle classe devant être créée pour chaque nouveau contrat de données, un mécanisme est donc nécessaire pour éviter d'avoir à utiliser le code existant qui a été écrit par rapport à l'ancienne classe de contrat de données et à le réécrire par rapport à la nouvelle.  
  
 Un mécanisme de ce type permet d'utiliser des interfaces pour définir les membres de chaque contrat de données et écrire le code d'implémentation interne par rapport aux interfaces plutôt que par rapport aux classes de contrat de données qui implémentent les interfaces. Le code suivant de la version 1 d'un service présente une interface `IPurchaseOrderV1` et `PurchaseOrderV1` :  
  
```csharp  
public interface IPurchaseOrderV1  
{  
    string OrderId { get; set; }  
    string CustomerId { get; set; }  
}  
  
[DataContract(  
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2005/10/PurchaseOrder")]  
public class PurchaseOrderV1 : IPurchaseOrderV1  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
}  
```  
  
 Alors que les opérations du contrat de service sont écrites par rapport à `PurchaseOrderV1`, la logique métier réelle est écrite par rapport à `IPurchaseOrderV1`. Puis, dans la version 2, il y aurait une nouvelle interface `IPurchaseOrderV2` et une nouvelle classe `PurchaseOrderV2`, tel qu'indiqué dans le code suivant :  
  
```csharp
public interface IPurchaseOrderV2  
{  
    DateTime OrderDate { get; set; }  
}

[DataContract(
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2006/02/PurchaseOrder")]  
public class PurchaseOrderV2 : IPurchaseOrderV1, IPurchaseOrderV2  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
    [DataMember(...)]  
    public DateTime OrderDate { ... }  
}  
```  
  
 Le contrat de service est mis à jour afin d'inclure les nouvelles opérations écrites par rapport à `PurchaseOrderV2`. La logique métier existante écrite par rapport à `IPurchaseOrderV1` continue à fonctionner pour `PurchaseOrderV2`, et la nouvelle logique métier qui nécessite la propriété `OrderDate` est écrite par rapport à `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Data Contract Equivalence](./feature-details/data-contract-equivalence.md)
- [Rappels de sérialisation avec tolérance de version](./feature-details/version-tolerant-serialization-callbacks.md)
