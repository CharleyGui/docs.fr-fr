---
title: 'Procédure : créer un contrat de données de base pour une classe ou structure'
description: Suivez cet exemple pour apprendre à créer un contrat de données à l’aide d’une classe ou d’une structure dans WCF à l’aide de l’attribut DataContractAttribute.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 5634eb3d3ec18d95fd7d6b3c89b572ab4f5b8eca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254036"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="437a5-103">Procédure : créer un contrat de données de base pour une classe ou structure</span><span class="sxs-lookup"><span data-stu-id="437a5-103">How to: Create a Basic Data Contract for a Class or Structure</span></span>

<span data-ttu-id="437a5-104">Cette rubrique illustre les étapes de base pour créer un contrat de données à l'aide d'une classe ou d'une structure.</span><span class="sxs-lookup"><span data-stu-id="437a5-104">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="437a5-105">Pour plus d’informations sur les contrats de données et leur utilisation, consultez [utilisation de contrats de données](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="437a5-105">For more information about data contracts and how they are used, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="437a5-106">Pour obtenir un didacticiel qui vous guide tout au long des étapes de création d’un client et d’un service de base Windows Communication Foundation (WCF), consultez le [didacticiel prise en main](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="437a5-106">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="437a5-107">Pour obtenir un exemple d’application fonctionnel qui se compose d’un service et d’un client de base, consultez [contrat de données de base](../samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="437a5-107">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="437a5-108">Pour créer un contrat de données de base destiné à une classe ou une structure</span><span class="sxs-lookup"><span data-stu-id="437a5-108">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="437a5-109">Déclarez que le type a un contrat de données en appliquant l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à la classe.</span><span class="sxs-lookup"><span data-stu-id="437a5-109">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="437a5-110">Notez que tous les types publics, y compris ceux sans attributs, sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="437a5-110">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="437a5-111">Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données si l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> est absent.</span><span class="sxs-lookup"><span data-stu-id="437a5-111">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="437a5-112">Pour plus d’informations, consultez [types sérialisables](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="437a5-112">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
2. <span data-ttu-id="437a5-113">Définissez les membres (propriétés, champs ou événements) sérialisés en appliquant l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à chaque membre.</span><span class="sxs-lookup"><span data-stu-id="437a5-113">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="437a5-114">Ces membres sont appelés des membres de données.</span><span class="sxs-lookup"><span data-stu-id="437a5-114">These members are called data members.</span></span> <span data-ttu-id="437a5-115">Par défaut, tous les types publics sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="437a5-115">By default, all public types are serializable.</span></span> <span data-ttu-id="437a5-116">Pour plus d’informations, consultez [types sérialisables](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="437a5-116">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="437a5-117">Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> aux champs privés, ce qui expose les données aux autres.</span><span class="sxs-lookup"><span data-stu-id="437a5-117">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="437a5-118">Vérifiez que le membre ne contient pas de données sensibles.</span><span class="sxs-lookup"><span data-stu-id="437a5-118">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="437a5-119"> Exemple</span><span class="sxs-lookup"><span data-stu-id="437a5-119">Example</span></span>  

 <span data-ttu-id="437a5-120">L'exemple suivant montre comment créer un contrat de données pour le type `Person` en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> à la classe et à ses membres.</span><span class="sxs-lookup"><span data-stu-id="437a5-120">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="437a5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="437a5-121">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="437a5-122">Utilisation de contrats de données</span><span class="sxs-lookup"><span data-stu-id="437a5-122">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="437a5-123">Didacticiel de mise en route</span><span class="sxs-lookup"><span data-stu-id="437a5-123">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="437a5-124">Prise en main</span><span class="sxs-lookup"><span data-stu-id="437a5-124">Getting Started</span></span>](../samples/getting-started-sample.md)
