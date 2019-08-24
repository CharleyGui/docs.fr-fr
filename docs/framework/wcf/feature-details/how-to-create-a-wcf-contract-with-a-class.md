---
title: 'Procédure : Créer un contrat de Windows Communication Foundation avec une classe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 2cd757107d9f62ce749d98db1d4968c02a09c5d2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988748"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Procédure : Créer un contrat de Windows Communication Foundation avec une classe
La méthode recommandée pour créer un contrat Windows Communication Foundation (WCF) consiste à utiliser une interface. Pour plus d’informations, consultez [Guide pratique pour Définir un contrat](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)de service. Une autre solution, présentée dans cette rubrique, consiste à créer une classe, à appliquer l'attribut <xref:System.ServiceModel.ServiceContractAttribute> directement sur celle-ci, puis l'attribut <xref:System.ServiceModel.OperationContractAttribute> sur chacune des méthodes de la classe qui font partie du contrat.  
  
> [!WARNING]
> `[ServiceContract]` et `[ServiceContractAttribute]` produisent le même résultat. La même chose est vraie pour `[OperationContract]` et `[OperationContractAttribute]`. Dans chaque cas, le premier est raccourci pour le deuxième.  
  
 Pour plus d’informations sur les contrats de service, consultez [conception de contrats de service](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Création d'un contrat Windows Communication Foundation à l'aide d'une classe  
  
1. Créez une classe à l’aide de C#Visual Basic, ou tout autre langage de Common Language Runtime.  
  
2. Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à la classe.  
  
3. Créez des méthodes dans la classe.  
  
4. Appliquez la <xref:System.ServiceModel.OperationContractAttribute> classe à chaque méthode qui doit être exposée dans le cadre du contrat WCF public.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant présente une classe qui définit un contrat de service.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande-réponse par défaut. Pour plus d’informations sur ce modèle de message [, consultez Procédure: Créez un contrat](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)de demande-réponse. Vous pouvez également créer et utiliser d'autres modèles de message en définissant les propriétés de l'attribut. Pour plus d'exemples, consultez [Procédure : Créez un contrat](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) unidirectionnel et [Comment: Créez un contrat](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)duplex.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
