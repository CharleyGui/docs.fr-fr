---
title: 'Comment : créer un service qui requiert des sessions'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184989"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Comment : créer un service qui requiert des sessions
Les sessions créent un état partagé entre deux ou plusieurs points de terminaison activant des fonctions utiles telles que les rappels, la sécurité en cascade et des associations entre clients et instances de service. Pour plus d’informations sur les sessions dans les applications de la Windows Communication Foundation (WCF), voir [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Pour spécifier qu'un contrat requiert que sa liaison prenne en charge des sessions  
  
1. Créez un contrat de service qui contient au moins une opération. Par exemple, comment créer un contrat de service, voir [comment : Définir un contrat de service](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. Modifiez le <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> qui déclare le contrat en affectant à la propriété <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> la valeur :  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> si ce contrat doit être exécuté dans une session.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> si ce contrat peut être exécuté dans une session.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> si ce contrat ne doit pas être exécuté dans une session.  
  
3. Configurez votre point de terminaison de service pour utiliser une liaison qui prend en charge des sessions. L'exemple de configuration suivant montre l'utilisation de <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, qui prend en charge une session de messagerie WS`-`Reliable.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a> Exemple  
 Le code d’exemple suivant indique comment utiliser une exigence de session au niveau du contrat et utiliser un fichier de configuration pour prendre en charge cette exigence avec la liaison <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
