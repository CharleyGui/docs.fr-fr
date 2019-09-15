---
title: 'Procédure : spécifier une liaison de client dans le code'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990232"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Procédure : spécifier une liaison de client dans le code
Dans cet exemple, un client est créé afin d’utiliser un service de calculatrice et la liaison du client est spécifiée de manière impérative dans le code. Le client accède au service `CalculatorService`, lequel implémente l'interface `ICalculator`. Le service et le client utilisent la classe <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Cette procédure part du principe que le service de calculatrice est en cours d'exécution. Pour plus d’informations sur la création du [service, consultez Procédure : Spécifiez une liaison de service](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)dans la configuration. Il utilise également l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) fournit pour générer automatiquement les composants du client. Cet outil génère le code client permettant d'accéder au service.  
  
 La construction du client se divise en deux parties. L'outil Svcutil.exe génère la calculatrice `ClientCalculator` qui implémente l'interface `ICalculator`. Cette application cliente est ensuite créée en construisant une instance de `ClientCalculator`, puis en spécifiant la liaison et l'adresse du service dans le code.  
  
 Pour obtenir la copie source de cet exemple, consultez l’exemple [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) .  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Pour spécifier une liaison personnalisée dans le code  
  
1. Utilisez l'outil Svcutil.exe depuis la ligne de commande pour générer le code à partir des métadonnées de service.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Le client généré contient également l'implémentation de `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Créez une instance de `ClientCalculator` qui utilise la classe <xref:System.ServiceModel.BasicHttpBinding> dans une application cliente. Appelez ensuite les opérations de service au niveau de l'adresse spécifiée.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Compilez, puis exécutez le client.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
