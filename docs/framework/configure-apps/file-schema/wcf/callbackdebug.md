---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 02632cc3f668bb9e4cc6f8c9726d7bcb3cab2c5d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183817"
---
# \<callbackDebug>

<span data-ttu-id="235a2-101">Spécifie le débogage de service pour un objet de rappel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="235a2-101">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="235a2-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="235a2-102">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="235a2-103">Type</span><span class="sxs-lookup"><span data-stu-id="235a2-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="235a2-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="235a2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="235a2-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="235a2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="235a2-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="235a2-106">Attributes</span></span>  
  
|<span data-ttu-id="235a2-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="235a2-107">Attribute</span></span>|<span data-ttu-id="235a2-108">Description</span><span class="sxs-lookup"><span data-stu-id="235a2-108">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="235a2-109">Valeur qui spécifie si les objets de rappel client retournent au service des informations sur les exceptions managées dans les erreurs SOAP.</span><span class="sxs-lookup"><span data-stu-id="235a2-109">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="235a2-110">Si vous définissez cet attribut par programme à `true`, vous pouvez activer le retour du flux d'informations sur les exceptions managées dans un objet de rappel client, à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="235a2-110">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="235a2-111">**Attention :**  Le retour d’informations sur les exceptions managées aux clients peut être un risque pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="235a2-111">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="235a2-112">En effet, les détails de l'exception exposent des informations relatives à l'implémentation d'un service interne qui peuvent être utilisées par des clients non autorisés.</span><span class="sxs-lookup"><span data-stu-id="235a2-112">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="235a2-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="235a2-113">Child Elements</span></span>  

 <span data-ttu-id="235a2-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="235a2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="235a2-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="235a2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="235a2-116">Élément</span><span class="sxs-lookup"><span data-stu-id="235a2-116">Element</span></span>|<span data-ttu-id="235a2-117">Description</span><span class="sxs-lookup"><span data-stu-id="235a2-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="235a2-118">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="235a2-118">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="235a2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="235a2-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
