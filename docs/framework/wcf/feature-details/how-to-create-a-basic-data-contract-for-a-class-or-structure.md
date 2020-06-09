---
title: 'Comment : créer un contrat de données de base destiné à une classe ou une structure'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 0fd7bbea4d6e8d315566aa798ed89a0fd2657f58
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599033"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="4deb1-102">Comment : créer un contrat de données de base destiné à une classe ou une structure</span><span class="sxs-lookup"><span data-stu-id="4deb1-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="4deb1-103">Cette rubrique illustre les étapes de base pour créer un contrat de données à l'aide d'une classe ou d'une structure.</span><span class="sxs-lookup"><span data-stu-id="4deb1-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="4deb1-104">Pour plus d’informations sur les contrats de données et leur utilisation, consultez [utilisation de contrats de données](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="4deb1-104">For more information about data contracts and how they are used, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="4deb1-105">Pour obtenir un didacticiel qui vous guide tout au long des étapes de création d’un client et d’un service de base Windows Communication Foundation (WCF), consultez le [didacticiel prise en main](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="4deb1-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="4deb1-106">Pour obtenir un exemple d’application fonctionnel qui se compose d’un service et d’un client de base, consultez [contrat de données de base](../samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="4deb1-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="4deb1-107">Pour créer un contrat de données de base destiné à une classe ou une structure</span><span class="sxs-lookup"><span data-stu-id="4deb1-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="4deb1-108">Déclarez que le type a un contrat de données en appliquant l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à la classe.</span><span class="sxs-lookup"><span data-stu-id="4deb1-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="4deb1-109">Notez que tous les types publics, y compris ceux sans attributs, sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="4deb1-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="4deb1-110">Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données si l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> est absent.</span><span class="sxs-lookup"><span data-stu-id="4deb1-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="4deb1-111">Pour plus d’informations, consultez [types sérialisables](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="4deb1-111">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
2. <span data-ttu-id="4deb1-112">Définissez les membres (propriétés, champs ou événements) sérialisés en appliquant l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à chaque membre.</span><span class="sxs-lookup"><span data-stu-id="4deb1-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="4deb1-113">Ces membres sont appelés des membres de données.</span><span class="sxs-lookup"><span data-stu-id="4deb1-113">These members are called data members.</span></span> <span data-ttu-id="4deb1-114">Par défaut, tous les types publics sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="4deb1-114">By default, all public types are serializable.</span></span> <span data-ttu-id="4deb1-115">Pour plus d’informations, consultez [types sérialisables](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="4deb1-115">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4deb1-116">Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> aux champs privés, ce qui expose les données aux autres.</span><span class="sxs-lookup"><span data-stu-id="4deb1-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="4deb1-117">Vérifiez que le membre ne contient pas de données sensibles.</span><span class="sxs-lookup"><span data-stu-id="4deb1-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4deb1-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="4deb1-118">Example</span></span>  
 <span data-ttu-id="4deb1-119">L'exemple suivant montre comment créer un contrat de données pour le type `Person` en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> à la classe et à ses membres.</span><span class="sxs-lookup"><span data-stu-id="4deb1-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4deb1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4deb1-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="4deb1-121">Using Data Contracts</span><span class="sxs-lookup"><span data-stu-id="4deb1-121">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="4deb1-122">Didacticiel Prise en main</span><span class="sxs-lookup"><span data-stu-id="4deb1-122">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="4deb1-123">Prise en main</span><span class="sxs-lookup"><span data-stu-id="4deb1-123">Getting Started</span></span>](../samples/getting-started-sample.md)
