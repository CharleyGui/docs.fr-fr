---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 46f2872fb289c2793c356ea179deb3ce52e6d65e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855310"
---
# <a name="exposedmethod"></a><span data-ttu-id="dc3d2-101">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="dc3d2-101">\<exposedMethod></span></span>
<span data-ttu-id="dc3d2-102">Représente une méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="dc3d2-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
<span data-ttu-id="dc3d2-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dc3d2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dc3d2-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dc3d2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dc3d2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comconventions**](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="dc3d2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="dc3d2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="dc3d2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="dc3d2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<exposedMethods >** ](exposedmethods.md)</span><span class="sxs-lookup"><span data-stu-id="dc3d2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)</span></span>\
<span data-ttu-id="dc3d2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<exposedMethod >**</span><span class="sxs-lookup"><span data-stu-id="dc3d2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3d2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc3d2-109">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc3d2-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dc3d2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dc3d2-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dc3d2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc3d2-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="dc3d2-112">Attributes</span></span>  
  
|<span data-ttu-id="dc3d2-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="dc3d2-113">Attribute</span></span>|<span data-ttu-id="dc3d2-114">Description</span><span class="sxs-lookup"><span data-stu-id="dc3d2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc3d2-115">name</span><span class="sxs-lookup"><span data-stu-id="dc3d2-115">name</span></span>|<span data-ttu-id="dc3d2-116">Chaîne qui contient la méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée comme un service Web.</span><span class="sxs-lookup"><span data-stu-id="dc3d2-116">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc3d2-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dc3d2-117">Child Elements</span></span>  
 <span data-ttu-id="dc3d2-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dc3d2-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc3d2-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dc3d2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dc3d2-120">Élément</span><span class="sxs-lookup"><span data-stu-id="dc3d2-120">Element</span></span>|<span data-ttu-id="dc3d2-121">Description</span><span class="sxs-lookup"><span data-stu-id="dc3d2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc3d2-122">\<exposedMethods></span><span class="sxs-lookup"><span data-stu-id="dc3d2-122">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="dc3d2-123">Collection d' [ \<éléments > ExposedMethod](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="dc3d2-123">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc3d2-124">Notes</span><span class="sxs-lookup"><span data-stu-id="dc3d2-124">Remarks</span></span>  
 <span data-ttu-id="dc3d2-125">Il est possible d'utiliser l'outil de configuration d'intégration COM+ (ComSvcConfig.exe) pour ajouter des méthodes spécifiques issues d'une interface COM afin qu'elles apparaissent sur le contrat de service généré.</span><span class="sxs-lookup"><span data-stu-id="dc3d2-125">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="dc3d2-126">Par exemple, vous pouvez utiliser la commande suivante pour ajouter les trois méthodes nommées issues de l'interface COM `IFinances` sur le composant financier `ItemOrders` au contrat de service généré.</span><span class="sxs-lookup"><span data-stu-id="dc3d2-126">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="dc3d2-127">Quand vous exécutez également le fichier ComSvcConfig. exe, il génère le contrat de service suivant, qui répertorie les méthodes mentionnées précédemment comme [ \<ExposedMethod >](exposedmethod.md) Elements.</span><span class="sxs-lookup"><span data-stu-id="dc3d2-127">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="dc3d2-128">Au moment de l’initialisation du service, le runtime tente de générer un contrat de service en reflétant et en ajoutant uniquement les méthodes incluses dans la liste des éléments de [ \<> ExposedMethod](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="dc3d2-128">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="dc3d2-129">Une trace est produite pour chaque méthode d'interface qui n'est pas incluse sur le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="dc3d2-129">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc3d2-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc3d2-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="dc3d2-131">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="dc3d2-131">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="dc3d2-132">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="dc3d2-132">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="dc3d2-133">Guide pratique pour Configurer les paramètres du service COM+</span><span class="sxs-lookup"><span data-stu-id="dc3d2-133">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
