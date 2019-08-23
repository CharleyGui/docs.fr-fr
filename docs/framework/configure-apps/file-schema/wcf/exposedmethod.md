---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 032139b714aa11079c7ee8610c332e404b3981ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918996"
---
# <a name="exposedmethod"></a><span data-ttu-id="bdfdb-101">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="bdfdb-101">\<exposedMethod></span></span>
<span data-ttu-id="bdfdb-102">Représente une méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="bdfdb-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="bdfdb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bdfdb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bdfdb-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="bdfdb-104">\<comContracts></span></span>  
<span data-ttu-id="bdfdb-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="bdfdb-105">\<comContract></span></span>  
<span data-ttu-id="bdfdb-106">\<methods></span><span class="sxs-lookup"><span data-stu-id="bdfdb-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdfdb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdfdb-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdfdb-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bdfdb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bdfdb-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bdfdb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdfdb-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="bdfdb-110">Attributes</span></span>  
  
|<span data-ttu-id="bdfdb-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="bdfdb-111">Attribute</span></span>|<span data-ttu-id="bdfdb-112">Description</span><span class="sxs-lookup"><span data-stu-id="bdfdb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bdfdb-113">name</span><span class="sxs-lookup"><span data-stu-id="bdfdb-113">name</span></span>|<span data-ttu-id="bdfdb-114">Chaîne qui contient la méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée comme un service Web.</span><span class="sxs-lookup"><span data-stu-id="bdfdb-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdfdb-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bdfdb-115">Child Elements</span></span>  
 <span data-ttu-id="bdfdb-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bdfdb-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdfdb-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bdfdb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bdfdb-118">Élément</span><span class="sxs-lookup"><span data-stu-id="bdfdb-118">Element</span></span>|<span data-ttu-id="bdfdb-119">Description</span><span class="sxs-lookup"><span data-stu-id="bdfdb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdfdb-120">\<exposedMethods></span><span class="sxs-lookup"><span data-stu-id="bdfdb-120">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="bdfdb-121">Collection d' [ \<éléments > ExposedMethod](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="bdfdb-121">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdfdb-122">Notes</span><span class="sxs-lookup"><span data-stu-id="bdfdb-122">Remarks</span></span>  
 <span data-ttu-id="bdfdb-123">Il est possible d'utiliser l'outil de configuration d'intégration COM+ (ComSvcConfig.exe) pour ajouter des méthodes spécifiques issues d'une interface COM afin qu'elles apparaissent sur le contrat de service généré.</span><span class="sxs-lookup"><span data-stu-id="bdfdb-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="bdfdb-124">Par exemple, vous pouvez utiliser la commande suivante pour ajouter les trois méthodes nommées issues de l'interface COM `IFinances` sur le composant financier `ItemOrders` au contrat de service généré.</span><span class="sxs-lookup"><span data-stu-id="bdfdb-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="bdfdb-125">Quand vous exécutez également le fichier ComSvcConfig. exe, il génère le contrat de service suivant, qui répertorie les méthodes mentionnées précédemment comme [ \<ExposedMethod >](exposedmethod.md) Elements.</span><span class="sxs-lookup"><span data-stu-id="bdfdb-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="bdfdb-126">Au moment de l’initialisation du service, le runtime tente de générer un contrat de service en reflétant et en ajoutant uniquement les méthodes incluses dans la liste des éléments de [ \<> ExposedMethod](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="bdfdb-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="bdfdb-127">Une trace est produite pour chaque méthode d'interface qui n'est pas incluse sur le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="bdfdb-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfdb-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdfdb-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="bdfdb-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="bdfdb-129">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="bdfdb-130">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="bdfdb-130">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="bdfdb-131">Guide pratique pour Configurer les paramètres du service COM+</span><span class="sxs-lookup"><span data-stu-id="bdfdb-131">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
