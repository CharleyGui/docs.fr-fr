---
title: 'Procédure : Appeler des opérations de Service WCF de façon asynchrone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: aba41d707426f29c2bcd626dbbe13d16d9e1b1f7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624508"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Procédure : Appeler des opérations de Service WCF de façon asynchrone
Cette rubrique présente comment un client peut accéder de façon asynchrone à une opération de service. Le service dans cette rubrique implémente l'interface `ICalculator`. Le client peut appeler les opérations sur cette interface de manière asynchrone à l'aide du modèle d'appel asynchrone commandé par événement. (Pour plus d’informations sur le modèle d’appel asynchrone basé sur des événements, consultez [programmation multithread avec le modèle asynchrone basé sur événement](https://go.microsoft.com/fwlink/?LinkId=248184)). Pour obtenir un exemple qui montre comment implémenter une opération de façon asynchrone dans un service, consultez [Comment : Implémenter une opération de Service asynchrone](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Pour plus d’informations sur les opérations synchrones et asynchrones, consultez [synchrone et opérations asynchrones](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Le modèle d'appel asynchrone commandé par événement n'est pas pris en charge lorsqu'il utilise un <xref:System.ServiceModel.ChannelFactory%601>. Pour plus d’informations sur les appels asynchrones à l’aide de la <xref:System.ServiceModel.ChannelFactory%601>, consultez [Comment : Appeler des opérations de façon asynchrone à l’aide d’une fabrique de canaux](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Pour appeler des opérations de service WCF de façon asynchrone  
  
1. Exécutez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil avec les deux le `/async` et le `/tcv:Version35` commande options ensemble, comme indiqué dans la commande suivante.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Cette opération génère en plus les opérations synchrones et standards en fonction de délégué asynchrones, une classe de client WCF qui contient :  
  
    - Deux <`operationName` > `Async` opérations pour une utilisation avec l’approche appel asynchrone basé sur des événements. Exemple :  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Événements terminés d’opérations sous la forme <`operationName` > `Completed` pour une utilisation avec l’approche appel asynchrone basé sur des événements. Exemple :  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType> types pour chaque opération (sous la forme <`operationName`>`CompletedEventArgs`) pour une utilisation avec l’approche appel asynchrone basé sur des événements. Exemple :  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. Dans l'application d'appel, créez une méthode de rappel à appeler au terme de l'opération asynchrone en vous conformant à l'exemple de code suivant.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. Avant d’appeler l’opération, utilisez un nouveau générique <xref:System.EventHandler%601?displayProperty=nameWithType> de type <`operationName` > `EventArgs` pour ajouter la méthode de gestionnaire (créée à l’étape précédente) à la <`operationName` > `Completed` événement. Appelez ensuite la <`operationName` > `Async` (méthode). Exemple :  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Exemple  
  
> [!NOTE]
>  Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>. Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>. Pour recevoir l'objet message comme la propriété `Result` et que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande `/messageContract`. Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>. Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Implémenter une opération de Service asynchrone](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
