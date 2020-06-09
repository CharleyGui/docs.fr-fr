---
title: 'Comment : créer un service avec une interface de contrat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597161"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Comment : créer un service avec une interface de contrat
La méthode recommandée pour créer un contrat Windows Communication Foundation (WCF) consiste à utiliser une interface. Ce contrat spécifie la collection et la structure des messages requis pour accéder aux opérations offertes par le service. Cette interface définit les types d'entrée et de sortie en appliquant la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface et la classe <xref:System.ServiceModel.OperationContractAttribute> aux méthodes que vous souhaitez exposer.  
  
 Pour plus d’informations sur les contrats de service, consultez [conception de contrats de service](../designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Création d'un contrat WCF avec une interface  
  
1. Créez une interface à l’aide de Visual Basic, C# ou tout autre langage de common language runtime.  
  
2. Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.  
  
3. Définissez les méthodes dans l'interface.  
  
4. Appliquez la <xref:System.ServiceModel.OperationContractAttribute> classe à chaque méthode qui doit être exposée dans le cadre du contrat WCF public.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant présente une interface qui définit un contrat de service.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande-réponse par défaut. Pour plus d’informations sur ce modèle de message, consultez [Comment : créer un contrat de demande-réponse](how-to-create-a-request-reply-contract.md). Vous pouvez également créer et utiliser d'autres modèles de message en définissant les propriétés de l'attribut. Pour obtenir plus d’exemples, consultez [Comment : créer un contrat unidirectionnel](how-to-create-a-one-way-contract.md) et [Comment : créer un contrat duplex](how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
