---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 2947f0de6a88f39463e58a3b39bda52588fe4baa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203902"
---
# \<exposedMethod>

<span data-ttu-id="a4940-101">Représente une méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="a4940-101">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a><span data-ttu-id="a4940-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4940-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4940-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a4940-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a4940-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a4940-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4940-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="a4940-105">Attributes</span></span>  
  
|<span data-ttu-id="a4940-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="a4940-106">Attribute</span></span>|<span data-ttu-id="a4940-107">Description</span><span class="sxs-lookup"><span data-stu-id="a4940-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4940-108">name</span><span class="sxs-lookup"><span data-stu-id="a4940-108">name</span></span>|<span data-ttu-id="a4940-109">Chaîne qui contient la méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée comme un service Web.</span><span class="sxs-lookup"><span data-stu-id="a4940-109">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4940-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a4940-110">Child Elements</span></span>  

 <span data-ttu-id="a4940-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a4940-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4940-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a4940-112">Parent Elements</span></span>  
  
|<span data-ttu-id="a4940-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a4940-113">Element</span></span>|<span data-ttu-id="a4940-114">Description</span><span class="sxs-lookup"><span data-stu-id="a4940-114">Description</span></span>|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|<span data-ttu-id="a4940-115">Collection d' [\<exposedMethod>](exposedmethod.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="a4940-115">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4940-116">Notes</span><span class="sxs-lookup"><span data-stu-id="a4940-116">Remarks</span></span>  

 <span data-ttu-id="a4940-117">Il est possible d'utiliser l'outil de configuration d'intégration COM+ (ComSvcConfig.exe) pour ajouter des méthodes spécifiques issues d'une interface COM afin qu'elles apparaissent sur le contrat de service généré.</span><span class="sxs-lookup"><span data-stu-id="a4940-117">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="a4940-118">Par exemple, vous pouvez utiliser la commande suivante pour ajouter les trois méthodes nommées issues de l'interface COM `IFinances` sur le composant financier `ItemOrders` au contrat de service généré.</span><span class="sxs-lookup"><span data-stu-id="a4940-118">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="a4940-119">Quand vous exécutez également le ComSvcConfig.exe, il génère le contrat de service suivant, qui répertorie les méthodes mentionnées précédemment comme des [\<exposedMethod>](exposedmethod.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="a4940-119">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="a4940-120">Au moment de l’initialisation du service, le runtime tente de générer un contrat de service en reflétant et en ajoutant uniquement les méthodes incluses dans la liste d' [\<exposedMethod>](exposedmethod.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="a4940-120">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="a4940-121">Une trace est produite pour chaque méthode d'interface qui n'est pas incluse sur le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="a4940-121">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4940-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4940-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="a4940-123">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="a4940-123">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a4940-124">Procédure : configurer des paramètres de service COM+</span><span class="sxs-lookup"><span data-stu-id="a4940-124">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
