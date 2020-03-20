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
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="4a2c0-102">Configuration de la sérialisation dans un service de workflow</span><span class="sxs-lookup"><span data-stu-id="4a2c0-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="4a2c0-103">Les services de flux de travail sont les services de la <xref:System.Runtime.Serialization.DataContractSerializer> Windows Communication Foundation <xref:System.Xml.Serialization.XmlSerializer>(WCF) et ont donc la possibilité d’utiliser le (le défaut) ou le .</span><span class="sxs-lookup"><span data-stu-id="4a2c0-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="4a2c0-104">Lors de l'écriture de services en dehors du workflow, le type de sérialiseur à utiliser est spécifié dans le contrat de service ou d'opération.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="4a2c0-105">Lors de la création de services de flux de travail WCF, vous ne spécifiez pas ces contrats dans le code, mais plutôt ils sont générés à l’heure de l’exécution par inférence de contrat.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="4a2c0-106">Pour plus d’informations sur l’inférence du contrat, voir [Utiliser les contrats dans workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="4a2c0-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="4a2c0-107">Le sérialiseur est spécifié à l'aide de la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="4a2c0-108">Celle-ci peut être définie dans le concepteur comme le montre l'illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Définir la propriété SerializerOption dans la fenêtre des propriétés.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="4a2c0-110">Le sérialiseur peut également être défini dans le code, comme le montre l'exemple suivant,</span><span class="sxs-lookup"><span data-stu-id="4a2c0-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="4a2c0-111">Les types connus peuvent également être spécifiés dans des services de workflow.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="4a2c0-112">Pour plus d’informations sur les types connus, voir [Data Contract Known Types](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="4a2c0-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="4a2c0-113">Les types connus peuvent être spécifiés dans le concepteur ou dans du code.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="4a2c0-114">Pour spécifier les types connus dans le concepteur, cliquez sur le bouton <xref:System.ServiceModel.Activities.Receive> ellipsis à côté de la propriété KnownTypes dans la **fenêtre propriétés** pour une activité comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![Capture d’écran de la boîte de dialogue de propriété KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="4a2c0-116">Cela affiche l’éditeur de collections de type qui vous permet de rechercher et de spécifier les types connus.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Capture d’écran de l’éditeur de collections de type.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="4a2c0-118">Cliquez sur le nouveau lien **de type Ajouter** et utiliser la goutte vers le bas pour sélectionner ou rechercher un type à ajouter à la collection de types connus.</span><span class="sxs-lookup"><span data-stu-id="4a2c0-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="4a2c0-119">Pour spécifier des types connus dans le code, utilisez la propriété <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>, comme le montre l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4a2c0-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
