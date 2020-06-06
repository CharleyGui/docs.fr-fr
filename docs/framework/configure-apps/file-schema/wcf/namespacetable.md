---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855095"
---
# \<namespaceTable>

<span data-ttu-id="eab06-101">Représente une section de configuration qui permet de définir un ensemble d’éléments contenant des mappages espace de noms-préfixe qui peuvent ensuite être utilisés dans des filtres XPath pour le routage.</span><span class="sxs-lookup"><span data-stu-id="eab06-101">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="eab06-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eab06-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eab06-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eab06-103">Attributes and elements</span></span>

<span data-ttu-id="eab06-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eab06-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="eab06-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="eab06-105">Attributes</span></span>

<span data-ttu-id="eab06-106">Aucune</span><span class="sxs-lookup"><span data-stu-id="eab06-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="eab06-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eab06-107">Child elements</span></span>

|     | <span data-ttu-id="eab06-108">Description</span><span class="sxs-lookup"><span data-stu-id="eab06-108">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="eab06-109">Définit un mappage préfixe-espace de noms utilisé pour les expressions XPath.</span><span class="sxs-lookup"><span data-stu-id="eab06-109">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="eab06-110">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eab06-110">Parent elements</span></span>

|     | <span data-ttu-id="eab06-111">Description</span><span class="sxs-lookup"><span data-stu-id="eab06-111">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="eab06-112">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="eab06-112">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="eab06-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eab06-113">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
