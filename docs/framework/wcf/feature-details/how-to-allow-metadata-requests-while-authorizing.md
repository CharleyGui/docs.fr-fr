---
title: 'Procédure : autoriser les requêtes de métadonnées pendant l’autorisation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 9acc007ea7837f7b8e6c958fa81547fe4fa5b2c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257611"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Procédure : autoriser les requêtes de métadonnées pendant l’autorisation

Pendant l'autorisation personnalisée, il peut être nécessaire d'autoriser le traitement d'une demande de métadonnées. La rubrique suivante présente les étapes de validation d'une telle demande.  
  
 Pour plus d’informations sur l’autorisation Windows Communication Foundation (WCF), consultez [authorization](authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Pour autoriser les demandes de métadonnées pendant l'autorisation  
  
1. Créez une extension de la classe <xref:System.ServiceModel.ServiceAuthorizationManager>.  
  
2. Remplacez la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> . La méthode retourne la valeur `true` ou `false` selon que l'autorisation est accordée ou non. Les informations relatives à la procédure en cours se trouvent dans le <xref:System.ServiceModel.OperationContext> passé comme paramètre à la méthode.  
  
3. Dans la substitution, vérifiez le nom de contrat, l'espace de noms et l'action comme illustré dans l'exemple suivant. Si les conditions sont valides, retournez `true.`  
  
4. Utilisez le point d'extensibilité pour employer la classe. Pour plus d’informations, consultez [Comment : créer un gestionnaire d’autorisations personnalisé pour un service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a> Exemple  

 L'exemple suivant illustre une substitution de la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Autorisation](authorization-in-wcf.md)
- [Gestion des revendications et autorisation avec le modèle d'identité](managing-claims-and-authorization-with-the-identity-model.md)
