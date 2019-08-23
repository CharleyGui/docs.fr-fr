---
title: Rappels de sérialisation avec tolérance de version
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 0736f94b1fe1a91b20ee76da673e0bc139aa802a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959553"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="e89e4-102">Rappels de sérialisation avec tolérance de version</span><span class="sxs-lookup"><span data-stu-id="e89e4-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="e89e4-103">Le modèle de programmation de contrat de données prend entièrement en charge les méthodes de rappel de sérialisation avec tolérance de version que les classes <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> et <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="e89e4-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="e89e4-104">Attributs avec tolérance de version</span><span class="sxs-lookup"><span data-stu-id="e89e4-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="e89e4-105">Il existe quatre attributs de rappel.</span><span class="sxs-lookup"><span data-stu-id="e89e4-105">There are four callback attributes.</span></span> <span data-ttu-id="e89e4-106">Chaque attribut peut être appliqué à une méthode que le moteur de sérialisation/désérialisation appelle à différents moments.</span><span class="sxs-lookup"><span data-stu-id="e89e4-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="e89e4-107">Le tableau suivant explique quand utiliser chaque attribut.</span><span class="sxs-lookup"><span data-stu-id="e89e4-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="e89e4-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e89e4-108">Attribute</span></span>|<span data-ttu-id="e89e4-109">Lorsque la méthode correspondante est appelée</span><span class="sxs-lookup"><span data-stu-id="e89e4-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="e89e4-110">Appelé avant de sérialiser le type.</span><span class="sxs-lookup"><span data-stu-id="e89e4-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="e89e4-111">Appelé après avoir sérialisé le type.</span><span class="sxs-lookup"><span data-stu-id="e89e4-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="e89e4-112">Appelé avant de désérialiser le type.</span><span class="sxs-lookup"><span data-stu-id="e89e4-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="e89e4-113">Appelé après avoir désérialisé le type.</span><span class="sxs-lookup"><span data-stu-id="e89e4-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="e89e4-114">Les méthodes doivent accepter un paramètre <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="e89e4-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="e89e4-115">Ces méthodes sont principalement destinées à une utilisation avec le versioning ou l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="e89e4-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="e89e4-116">Pendant la désérialisation, aucun constructeur n'est appelé.</span><span class="sxs-lookup"><span data-stu-id="e89e4-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="e89e4-117">Par conséquent, des membres de données risquent de ne pas être initialisés correctement (avec les valeurs par défaut prévues) si les données de ces membres ne figurent pas dans le flux entrant, par exemple, si les données viennent d'une version antérieure d'un type auquel il manque certains membres de données.</span><span class="sxs-lookup"><span data-stu-id="e89e4-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="e89e4-118">Pour corriger ce problème, utilisez la méthode de rappel marquée avec <xref:System.Runtime.Serialization.OnDeserializingAttribute>, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e89e4-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="e89e4-119">Vous pouvez marquer uniquement une méthode par type avec chacun des attributs de rappel précédents.</span><span class="sxs-lookup"><span data-stu-id="e89e4-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e89e4-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="e89e4-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e89e4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e89e4-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="e89e4-122">Sérialisation avec tolérance de version</span><span class="sxs-lookup"><span data-stu-id="e89e4-122">Version Tolerant Serialization</span></span>](../../../standard/serialization/version-tolerant-serialization.md)
