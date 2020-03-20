---
title: Configuration de la sérialisation dans un service de workflow
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185345"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Configuration de la sérialisation dans un service de workflow
Les services de flux de travail sont les services de la <xref:System.Runtime.Serialization.DataContractSerializer> Windows Communication Foundation <xref:System.Xml.Serialization.XmlSerializer>(WCF) et ont donc la possibilité d’utiliser le (le défaut) ou le . Lors de l'écriture de services en dehors du workflow, le type de sérialiseur à utiliser est spécifié dans le contrat de service ou d'opération. Lors de la création de services de flux de travail WCF, vous ne spécifiez pas ces contrats dans le code, mais plutôt ils sont générés à l’heure de l’exécution par inférence de contrat. Pour plus d’informations sur l’inférence du contrat, voir [Utiliser les contrats dans workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  Le sérialiseur est spécifié à l'aide de la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>. Celle-ci peut être définie dans le concepteur comme le montre l'illustration suivante.  
  
 ![Définir la propriété SerializerOption dans la fenêtre des propriétés.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 Le sérialiseur peut également être défini dans le code, comme le montre l'exemple suivant,  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  Les types connus peuvent également être spécifiés dans des services de workflow. Pour plus d’informations sur les types connus, voir [Data Contract Known Types](data-contract-known-types.md). Les types connus peuvent être spécifiés dans le concepteur ou dans du code. Pour spécifier les types connus dans le concepteur, cliquez sur le bouton <xref:System.ServiceModel.Activities.Receive> ellipsis à côté de la propriété KnownTypes dans la **fenêtre propriétés** pour une activité comme indiqué dans l’illustration suivante.
  
 ![Capture d’écran de la boîte de dialogue de propriété KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Cela affiche l’éditeur de collections de type qui vous permet de rechercher et de spécifier les types connus.  
  
 ![Capture d’écran de l’éditeur de collections de type.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Cliquez sur le nouveau lien **de type Ajouter** et utiliser la goutte vers le bas pour sélectionner ou rechercher un type à ajouter à la collection de types connus. Pour spécifier des types connus dans le code, utilisez la propriété <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>, comme le montre l'exemple suivant :  
  
```csharp
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```
