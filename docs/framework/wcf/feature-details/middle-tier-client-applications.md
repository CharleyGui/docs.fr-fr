---
title: Applications clientes de niveau intermédiaire
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: c50223a55765f211dae710f96bffa7716ce36b32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598812"
---
# <a name="middle-tier-client-applications"></a>Applications clientes de niveau intermédiaire
Cette rubrique décrit les différents problèmes spécifiques aux applications clientes de niveau intermédiaire qui utilisent Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Augmenter les performances du client de niveau intermédiaire  
 Par rapport aux technologies de communication précédentes, telles que les services Web utilisant ASP.NET, la création d’une instance de client WCF peut être plus complexe en raison de l’ensemble riche de fonctionnalités de WCF. Par exemple, lorsqu'un objet <xref:System.ServiceModel.ChannelFactory%601> est ouvert, il peut établir une session sécurisée avec le service, procédure qui augmente le temps de démarrage pour l'instance cliente. En règle générale, ces fonctionnalités de fonctionnalités supplémentaires n’affectent pas les applications clientes de manière considérable puisque le client WCF effectue plusieurs appels, puis se ferme.  
  
 Toutefois, les applications clientes de niveau intermédiaire peuvent créer rapidement de nombreux objets clients WCF et, par conséquent, rencontrer des exigences d’initialisation plus élevées. Il existe deux approches principales pour accroître les performances des applications de niveau intermédiaire lors d'un appel des services :  
  
- Mettez en cache l’objet client WCF et réutilisez-le pour les appels ultérieurs, dans la mesure du possible.  
  
- Créez un <xref:System.ServiceModel.ChannelFactory%601> objet, puis utilisez cet objet pour créer de nouveaux objets de canal client WCF pour chaque appel.  
  
 Les problèmes à prendre en compte lors de l'utilisation de ces approches sont les suivants :  
  
- Si le service conserve un état spécifique au client à l’aide d’une session, vous ne pouvez pas réutiliser le client WCF de couche intermédiaire avec plusieurs demandes de couche client, car l’état du service est lié à celui du client de couche intermédiaire.  
  
- Si le service doit effectuer l’authentification pour chaque client, vous devez créer un nouveau client pour chaque demande entrante sur la couche intermédiaire au lieu de réutiliser le client WCF de couche intermédiaire (ou l’objet de canal du client WCF), car les informations d’identification du client de la couche intermédiaire ne peuvent pas être modifiées après la création du client WCF (ou <xref:System.ServiceModel.ChannelFactory%601> ).  
  
- Si les canaux et les clients créés par les canaux sont thread-safe, ils peuvent ne pas prendre en charge l'écriture simultanée de plusieurs messages sur la transmission. Si vous envoyez des messages volumineux, notamment pour la diffusion en continu, l'opération d'envoi peut bloquer l'exécution d'une autre opération d'envoi. Cette situation entraîne deux types de problèmes : un manque d'accès concurrentiel et le risque d'interblocage si le flux de contrôle retourne au service par l'intermédiaire du canal (autrement dit, le client partagé appelle un service dont le chemin d'accès au code entraîne un rappel au client partagé). Cela est vrai quel que soit le type de client WCF que vous réutilisez.  
  
- Vous devez traiter les canaux défaillants, que vous partagiez ou non le canal. Toutefois, lorsque les canaux sont réutilisés, un canal défaillant peut faire échouer plusieurs opérations de demande ou d'envoi en attente.  
  
 Pour obtenir un exemple illustrant les meilleures pratiques pour réutiliser un client pour plusieurs requêtes, consultez [liaison de données dans un client ASP.net](../samples/data-binding-in-an-aspnet-client.md).  
  
 De plus, vous pouvez augmenter les performances de démarrage pour les clients qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> pour générer et compiler le code de sérialisation pour ces types de données au moment de l'exécution qui peuvent ralentir les performances de démarrage. L' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation nécessaire à partir des assemblys compilés pour l’application. Pour plus d’informations, consultez [Comment : améliorer le temps de démarrage des applications clientes WCF à l’aide de XmlSerializer](startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Voir aussi

- [Accès aux services à l’aide d’un client WCF](accessing-services-using-a-client.md)
