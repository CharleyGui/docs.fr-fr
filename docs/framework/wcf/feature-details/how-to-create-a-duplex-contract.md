---
title: 'Procédure : créer un contrat duplex'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: c603694bca82cfc5852c875946f18f9782209e48
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638778"
---
# <a name="how-to-create-a-duplex-contract"></a>Procédure : créer un contrat duplex
Cette rubrique décrit les étapes de base pour créer des méthodes qui utilisent un contrat duplex (bidirectionnel). Un contrat duplex autorise les clients et les serveurs à communiquer entre eux indépendamment de sorte que l'un puisse initier des appels à l'autre. Le contrat duplex est un des trois modèles de message disponibles aux services Windows Communication Foundation (WCF). Les deux autres modèles de message sont unidirectionnels et demande/réponse. Un contrat duplex se compose de deux contrats unidirectionnels entre le client et le serveur et ne requiert pas que les appels de méthode soient corrélés. Utilisez ce type de contrat lorsque votre service doit demander au client plus d'informations ou déclencher explicitement des événements sur le client. Pour plus d’informations sur la création d’une application cliente pour un contrat duplex, consultez [Comment : Accéder aux Services avec un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Pour obtenir un exemple fonctionnel, consultez le [Duplex](../../../../docs/framework/wcf/samples/duplex.md) exemple.  
  
### <a name="to-create-a-duplex-contract"></a>Pour créer un contrat duplex  
  
1. Créez l'interface constitutive du côté serveur du contrat duplex.  
  
2. Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. Déclarez les signatures de méthode dans l'interface.  
  
4. Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque signature de méthode qui doit faire partie du contrat public.  
  
5. Créez l'interface de rappel qui définit le jeu des opérations que le service peut appeler sur le client.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. Déclarez les signatures de méthode dans l'interface de rappel.  
  
7. Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque signature de méthode qui doit faire partie du contrat public.  
  
8. Liez les deux interfaces dans un contrat duplex en affectant à la propriété <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> dans l'interface primaire le type de l'interface de rappel.  
  
### <a name="to-call-methods-on-the-client"></a>Pour appeler des méthodes sur le client  
  
1. Dans l'implémentation de service du contrat principal, déclarez une variable pour l'interface de rappel.  
  
2. Affectez à la variable la référence d'objet retournée par la méthode <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> de la classe <xref:System.ServiceModel.OperationContext>.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. Appelez les méthodes définies par l'interface de rappel.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant illustre la communication duplex. Le contrat du service contient des opérations de service pour avancer et reculer. Le contrat du client contient une opération de service pour indiquer sa position.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- Appliquer les attributs <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> permet la génération automatique de définitions de contrat de service dans WSDL (Web Services Description Language).  
  
- Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour récupérer le document WSDL et de code (facultatif) et de configuration pour un client.  
  
- Les points de terminaison qui exposent des services duplex doivent être sécurisés. Lorsqu'un service reçoit un message duplex, il consulte l'élément ReplyTo dans ce message entrant afin de déterminer où envoyer la réponse. Si le canal n'est pas sécurisé, un client non fiable peut envoyer un message malveillant avec le ReplyTo d'un ordinateur cible, ce qui peut entraîner à un déni de service de l'ordinateur cible. Avec les messages de réponse/demande normaux, ce problème ne se pose pas, parce que le ReplyTo est ignoré et la réponse est envoyée sur le canal sur lequel le message d'origine est arrivé.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Guide pratique pour Access Services avec un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Duplex](../../../../docs/framework/wcf/samples/duplex.md)
- [Conception et implémentation de services](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Guide pratique pour Définir un contrat de Service](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Session](../../../../docs/framework/wcf/samples/session.md)
