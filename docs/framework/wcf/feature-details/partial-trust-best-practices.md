---
title: Meilleures pratiques dans un environnement de confiance partielle
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: 7d5bcc7f9f179553188b4ce90c724dc0bd839670
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663036"
---
# <a name="partial-trust-best-practices"></a>Meilleures pratiques dans un environnement de confiance partielle

Cette rubrique décrit les meilleures pratiques lors de l’exécution de Windows Communication Foundation (WCF) dans un environnement de confiance partielle.

## <a name="serialization"></a>Sérialisation

Appliquez les pratiques suivantes lors de l'utilisation du <xref:System.Runtime.Serialization.DataContractSerializer> dans une application de confiance partielle.

- Tous les types sérialisables doivent être marqués explicitement avec l'attribut `[DataContract]`. Les techniques suivantes ne sont pas prises en charge dans un environnement de confiance partielle :

- Marquage des classes à sérialiser avec le <xref:System.SerializableAttribute>.

- L'implémentation de l'interface <xref:System.Runtime.Serialization.ISerializable> pour permettre à une classe de contrôler son processus de sérialisation.

### <a name="using-datacontractserializer"></a>Utilisation de DataContractSerializer

- Tous les types marqués avec l'attribut `[DataContract]` doivent être publics. Les types non publics ne peuvent pas être sérialisés dans un environnement de confiance partielle.

- Tous les membres `[DataContract]` dans un type `[DataContract]` sérialisable doivent être publics. Un type avec un `[DataMember]` non public ne peut pas être sérialisé dans un environnement de confiance partielle.

- Les méthodes qui gèrent des événements de sérialisation (telles que `OnSerializing`, `OnSerialized`, `OnDeserializing`et `OnDeserialized`) doivent être déclarées comme publiques. Toutefois, les implémentations explicites et implicites de <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> sont prises en charge.

- Les types `[DataContract]` implémentés dans les assemblys marqués avec <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ne doivent pas effectuer d'actions relatives à la sécurité dans le constructeur de type, étant donné que <xref:System.Runtime.Serialization.DataContractSerializer> n'appelle pas le constructeur de l'objet instancié récemment pendant la désérialisation. En particulier, les techniques de sécurité courantes suivantes doivent être évitées pour les types `[DataContract]` :

- Tenter de restreindre l'accès de confiance partielle en rendant le constructeur du type interne ou privé.

- Restreindre l'accès au type en ajoutant un `[LinkDemand]` au constructeur du type.

- Supposer que du fait de l'instanciation correcte de l'objet, les contrôles de validation appliqués par le constructeur ont réussi.

### <a name="using-ixmlserializable"></a>Utilisation de IXmlSerializable

Les meilleures pratiques suivantes s'appliquent aux types qui implémentent <xref:System.Xml.Serialization.IXmlSerializable> et sont sérialisés à l'aide du <xref:System.Runtime.Serialization.DataContractSerializer> :

- Les implémentations de méthode statique <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> doivent être `public`.

- Les méthodes d'instance qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable> doivent être `public`.

## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Utilisation de WCF à partir d'un code de plateforme d'un niveau de confiance suffisant qui autorise les appels d'appelants d'un niveau de confiance partiel

Le modèle de sécurité de confiance partielle WCF suppose que tout appelant d’une propriété ou une méthode publique de WCF s’exécute dans le contexte de sécurité (CAS) de l’accès de code de l’application d’hébergement. WCF suppose également ce contexte de sécurité qu’une seule application existe pour chaque <xref:System.AppDomain>, et que ce contexte est établi au niveau <xref:System.AppDomain> heure de création par un hôte approuvé (par exemple, par un appel à <xref:System.AppDomain.CreateDomain%2A> ou par le Gestionnaire d’applications ASP.NET).

Ce modèle de sécurité s'applique aux applications écrites par l'utilisateur qui ne peuvent pas déclarer des autorisations CAS supplémentaires, telles que l'exécution du code utilisateur dans une application ASP.NET de confiance moyenne. Toutefois, le code de plate-forme de niveau de confiance (par exemple, un assembly tiers qui est installé dans le global assembly cache et accepte les appels du code partiellement fiable) doit prendre prudence lors de l’appel à WCF pour le compte d’une application de confiance partielle pour Évitez d’introduire des failles de sécurité de niveau application.

Code de confiance totale doit éviter de modifier le jeu d’autorisations CAS du thread actuel (en appelant <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, ou <xref:System.Security.PermissionSet.Deny%2A>) avant d’appeler des API WCF pour le compte du code partiellement fiable. La déclaration ou le refus, ou toute création d'un contexte d'autorisation spécifique au thread qui est indépendant du contexte de sécurité au niveau de l'application, peut entraîner un comportement imprévu. Selon l'application, ce comportement peut provoquer des failles de sécurité au niveau de l'application.

Code qui appelle dans WCF à l’aide d’un contexte d’autorisation spécifique au thread doit être préparé à gérer les situations suivantes peuvent survenir :

- Le contexte de sécurité spécifique au thread ne peut pas être maintenu pour la durée de l'opération, ce qui provoque des exceptions de sécurité potentielles.

- Code WCF interne, ainsi que des rappels fourni par l’utilisateur peuvent s’exécuter dans un contexte de sécurité différent de celui sous lequel l’appel a été lancé à l’origine. Ces contextes sont les suivants :

  - Le contexte d'autorisation d'application.

  - N’importe quel contexte d’autorisation spécifique au thread créé précédemment par d’autres threads utilisateur utilisés pour appeler dans WCF pendant la durée de vie de l’en cours d’exécution <xref:System.AppDomain>.

WCF garantit que du code partiellement fiable ne peut pas obtenir les autorisations de confiance totale, sauf si ces autorisations sont déclarées par un composant de niveau de confiance suffisant avant l’appel des API publiques WCF. Toutefois, il ne garantit pas que les effets de la déclaration de la confiance totale sont isolés d'un thread, d'une opération ou d'une action utilisateur en particulier.

La meilleure pratique consiste à éviter de créer le contexte d'autorisation spécifique au thread en appelant <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A> ou <xref:System.Security.PermissionSet.Deny%2A>. Au lieu de cela, accordez ou refusez le privilège à l'application, afin qu'aucune méthode <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A> ou <xref:System.Security.PermissionSet.PermitOnly%2A> ne soit requise.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
