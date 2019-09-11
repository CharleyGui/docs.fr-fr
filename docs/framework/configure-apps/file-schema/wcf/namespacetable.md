---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855095"
---
# <a name="namespacetable"></a><span data-ttu-id="b6c1e-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="b6c1e-101">\<namespaceTable></span></span>

<span data-ttu-id="b6c1e-102">Représente une section de configuration qui permet de définir un ensemble d’éléments contenant des mappages espace de noms-préfixe qui peuvent ensuite être utilisés dans des filtres XPath pour le routage.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="b6c1e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b6c1e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b6c1e-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b6c1e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b6c1e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="b6c1e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="b6c1e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="b6c1e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6c1e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6c1e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6c1e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b6c1e-108">Attributes and elements</span></span>

<span data-ttu-id="b6c1e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6c1e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6c1e-110">Attributes</span></span>

<span data-ttu-id="b6c1e-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="b6c1e-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b6c1e-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b6c1e-112">Child elements</span></span>

|     | <span data-ttu-id="b6c1e-113">Description</span><span class="sxs-lookup"><span data-stu-id="b6c1e-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b6c1e-114"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="b6c1e-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="b6c1e-115">Définit un mappage préfixe-espace de noms utilisé pour les expressions XPath.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b6c1e-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b6c1e-116">Parent elements</span></span>

|     | <span data-ttu-id="b6c1e-117">Description</span><span class="sxs-lookup"><span data-stu-id="b6c1e-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b6c1e-118"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="b6c1e-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="b6c1e-119">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles Envoyer des messages à lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b6c1e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6c1e-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
