---
title: Configuration de la sérialisation dans un service de workflow
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 5076f3d377a656cb96909cf8df01591dc6ab72b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597538"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="8c78c-102">Configuration de la sérialisation dans un service de workflow</span><span class="sxs-lookup"><span data-stu-id="8c78c-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="8c78c-103">Les services de workflow sont des services Windows Communication Foundation (WCF). par conséquent, vous avez la possibilité d’utiliser l' <xref:System.Runtime.Serialization.DataContractSerializer> (valeur par défaut) ou l' <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8c78c-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="8c78c-104">Lors de l'écriture de services en dehors du workflow, le type de sérialiseur à utiliser est spécifié dans le contrat de service ou d'opération.</span><span class="sxs-lookup"><span data-stu-id="8c78c-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="8c78c-105">Lorsque vous créez des services de workflow WCF, vous ne spécifiez pas ces contrats dans le code, mais ils sont générés au moment de l’exécution par l’inférence de contrat.</span><span class="sxs-lookup"><span data-stu-id="8c78c-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="8c78c-106">Pour plus d’informations sur l’inférence de contrat, consultez [utilisation de contrats dans le workflow](using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8c78c-106">For more information about contract inference, see  [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="8c78c-107">Le sérialiseur est spécifié à l'aide de la propriété <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c78c-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="8c78c-108">Celle-ci peut être définie dans le concepteur comme le montre l'illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="8c78c-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Définition de la propriété SerializerOption dans la fenêtre Propriétés.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="8c78c-110">Le sérialiseur peut également être défini dans le code, comme le montre l'exemple suivant,</span><span class="sxs-lookup"><span data-stu-id="8c78c-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="8c78c-111">Les types connus peuvent également être spécifiés dans des services de workflow.</span><span class="sxs-lookup"><span data-stu-id="8c78c-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="8c78c-112">Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="8c78c-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="8c78c-113">Les types connus peuvent être spécifiés dans le concepteur ou dans du code.</span><span class="sxs-lookup"><span data-stu-id="8c78c-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="8c78c-114">Pour spécifier des types connus dans le concepteur, cliquez sur le bouton de sélection en regard de la propriété KnownTypes dans la **fenêtre Propriétés** d’une <xref:System.ServiceModel.Activities.Receive> activité, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="8c78c-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![Capture d’écran de la boîte de dialogue Propriétés de KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="8c78c-116">L’éditeur de collections de types s’affiche et vous permet de rechercher et de spécifier des types connus.</span><span class="sxs-lookup"><span data-stu-id="8c78c-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Capture d’écran de l’éditeur de collections de types.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="8c78c-118">Cliquez sur le lien **Ajouter un nouveau type** et utilisez la liste déroulante pour sélectionner ou Rechercher un type à ajouter à la collection de types connus.</span><span class="sxs-lookup"><span data-stu-id="8c78c-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="8c78c-119">Pour spécifier des types connus dans le code, utilisez la propriété <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A>, comme le montre l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8c78c-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
