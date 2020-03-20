---
title: Intégration de composants transactionnels Enterprise Services
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 292573f911459d8a8419e09d81fd1e54dbc6c70b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184739"
---
# <a name="integrating-enterprise-services-transactional-components"></a>Intégration de composants transactionnels Enterprise Services

Windows Communication Foundation (WCF) fournit un mécanisme automatique d’intégration avec les services aux entreprises (voir [Intégration avec les applications COMMD](integrating-with-com-plus-applications.md)). Cependant, vous préférez peut-être pouvoir développer des services utilisant en interne des composants transactionnels hébergés par Enterprise Services. Étant donné que la fonctionnalité <xref:System.Transactions> WCF Transactions est construite sur l’infrastructure, le processus d’intégration <xref:System.Transactions> des services aux entreprises avec WCF est identique à celui de la spécibilité entre et des services d’entreprise, tel qu’il est décrit dans [Interopérabilité avec les services d’entreprise et les transactions COMMD](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).  
  
 Afin d’offrir un niveau d’interopérabilité suffisant entre les transactions entrantes et les transactions de contexte COM+, l’implémentation de service doit créer une instance <xref:System.Transactions.TransactionScope> et utiliser la valeur appropriée de l’énumération <xref:System.Transactions.EnterpriseServicesInteropOption>.  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a>Intégration des composants Enterprise Services à une opération de service  
 L’exemple de code suivant contient une opération (autorisant le transfert des transactions) qui crée une étendue <xref:System.Transactions.TransactionScope> à l’aide de l’option <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. Les conditions suivantes s'appliquent à notre exemple :  
  
- Si le client transfère une transaction, l'opération, y compris l'appel au composant Enterprise Services, est exécutée dans les limites de portée de cette transaction. L’utilisation de <xref:System.Transactions.EnterpriseServicesInteropOption.Full> assure la synchronisation de la transaction avec le contexte <xref:System.EnterpriseServices>, ce qui signifie que la transaction ambiante de <xref:System.Transactions> correspond à celle de <xref:System.EnterpriseServices>.  
  
- Si le client ne transfère pas de transaction, affecter la valeur <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> à`true` attribue une nouvelle portée de transaction à l'opération. De la même façon, l'utilisation de <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garantit que la transaction de l'opération correspond à la transaction utilisée dans le contexte du composant <xref:System.EnterpriseServices>.  
  
 Tous les appels de méthode supplémentaires se produisent également dans les limites de portée de transaction de la même opération.  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services
         // component
  
         // Call UpdateOtherCustomerData method on an Enterprise
         // Services component
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 Si aucune synchronisation n'est requise entre la transaction en cours d'une opération et les appels aux composants transactionnels Enterprise Services, utilisez l'option <xref:System.Transactions.EnterpriseServicesInteropOption.None> lorsque vous instanciez l'instance <xref:System.Transactions.TransactionScope>.  
  
## <a name="integrating-enterprise-services-with-a-client"></a>Intégration des composants Enterprise Services à un client  
 L'exemple de code suivant contient un code client qui utilise une instance <xref:System.Transactions.TransactionScope> avec le paramètre <xref:System.Transactions.EnterpriseServicesInteropOption.Full>. Dans cet exemple de code, les appels aux opérations de service qui prennent en charge le transfert des transactions se produisent dans les mêmes limites de portée de transaction que les appels aux composants Enterprise Services, leurs transactions étant identiques.  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services
        // component
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Intégration avec les applications COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Intégration à des applications COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
