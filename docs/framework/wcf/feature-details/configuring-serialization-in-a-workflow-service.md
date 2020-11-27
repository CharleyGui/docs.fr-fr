---
title: Configuration de la sérialisation dans un service de workflow
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: d1cda33c8a469b4a54b6d282b99c07b23e91543e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284197"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Configuration de la sérialisation dans un service de workflow

Les services de workflow sont des services Windows Communication Foundation (WCF). par conséquent, vous avez la possibilité d’utiliser l' <xref:System.Runtime.Serialization.DataContractSerializer> (valeur par défaut) ou l' <xref:System.Xml.Serialization.XmlSerializer> . Lors de l'écriture de services en dehors du workflow, le type de sérialiseur à utiliser est spécifié dans le contrat de service ou d'opération. Lorsque vous créez des services de workflow WCF, vous ne spécifiez pas ces contrats dans le code, mais ils sont générés au moment de l’exécution par l’inférence de contrat. Pour plus d’informations sur l’inférence de contrat, consultez  [utilisation de contrats dans le workflow](using-contracts-in-workflow.md).  Le sérialiseur est spécifié à l'aide de la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>. Celle-ci peut être définie dans le concepteur comme le montre l'illustration suivante.  
  
 ![Définition de la propriété SerializerOption dans la fenêtre Propriétés.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
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
  
  Les types connus peuvent également être spécifiés dans des services de workflow. Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](data-contract-known-types.md). Les types connus peuvent être spécifiés dans le concepteur ou dans du code. Pour spécifier des types connus dans le concepteur, cliquez sur le bouton de sélection en regard de la propriété KnownTypes dans la **fenêtre Propriétés** d’une <xref:System.ServiceModel.Activities.Receive> activité, comme indiqué dans l’illustration suivante.
  
 ![Capture d’écran de la boîte de dialogue Propriétés de KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 L’éditeur de collections de types s’affiche et vous permet de rechercher et de spécifier des types connus.  
  
 ![Capture d’écran de l’éditeur de collections de types.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Cliquez sur le lien **Ajouter un nouveau type** et utilisez la liste déroulante pour sélectionner ou Rechercher un type à ajouter à la collection de types connus. Pour spécifier des types connus dans le code, utilisez la propriété <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>, comme le montre l'exemple suivant :  
  
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
