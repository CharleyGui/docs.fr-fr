---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735939"
---
# \<useManagedPresentation>
<span data-ttu-id="55f21-101">Élément de liaison utilisé pour communiquer avec un service d’émission de jeton de sécurité CardSpace qui prend en charge le profil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="55f21-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="55f21-102">Cet élément n'a aucun attribut et est présent en tant que commutateur vide.</span><span class="sxs-lookup"><span data-stu-id="55f21-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="55f21-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55f21-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55f21-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="55f21-104">Attributes and Elements</span></span>  
 <span data-ttu-id="55f21-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="55f21-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55f21-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="55f21-106">Attributes</span></span>  
 <span data-ttu-id="55f21-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="55f21-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55f21-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55f21-108">Child Elements</span></span>  
 <span data-ttu-id="55f21-109">Aucune</span><span class="sxs-lookup"><span data-stu-id="55f21-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55f21-110">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55f21-110">Parent Elements</span></span>  
  
|<span data-ttu-id="55f21-111">Élément</span><span class="sxs-lookup"><span data-stu-id="55f21-111">Element</span></span>|<span data-ttu-id="55f21-112">Description</span><span class="sxs-lookup"><span data-stu-id="55f21-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="55f21-113">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="55f21-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55f21-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="55f21-114">Remarks</span></span>  
 <span data-ttu-id="55f21-115">Cet élément est utilisé par un fournisseur d'identité pour exprimer dans sa stratégie le fait qu'il prend en charge le profil CardSpace de WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="55f21-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="55f21-116">Les fournisseurs d'identité qui publient une telle assertion de stratégie doivent être en mesure de publier des jetons selon ce profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="55f21-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f21-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55f21-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="55f21-118">Liaisons</span><span class="sxs-lookup"><span data-stu-id="55f21-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="55f21-119">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="55f21-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="55f21-120">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="55f21-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
