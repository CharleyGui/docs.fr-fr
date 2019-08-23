---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: d1a48fa2ed90999a66f4c1f84b7cfaa9a0e79f6a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940584"
---
# <a name="userdefinedtype"></a><span data-ttu-id="f47fb-101">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="f47fb-101">\<userDefinedType></span></span>
<span data-ttu-id="f47fb-102">Représente un type défini par l'utilisateur (UDT) à inclure dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="f47fb-102">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="f47fb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f47fb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f47fb-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="f47fb-104">\<comContracts></span></span>  
<span data-ttu-id="f47fb-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="f47fb-105">\<comContract></span></span>  
<span data-ttu-id="f47fb-106">\<userDefinedTypes></span><span class="sxs-lookup"><span data-stu-id="f47fb-106">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f47fb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f47fb-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f47fb-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f47fb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f47fb-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f47fb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f47fb-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="f47fb-110">Attributes</span></span>  
  
|<span data-ttu-id="f47fb-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="f47fb-111">Attribute</span></span>|<span data-ttu-id="f47fb-112">Description</span><span class="sxs-lookup"><span data-stu-id="f47fb-112">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="f47fb-113">Attribut facultatif qui contient une chaîne fournissant le nom de type lisible.</span><span class="sxs-lookup"><span data-stu-id="f47fb-113">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="f47fb-114">Il n'est pas utilisé par l'exécution mais aide le lecteur à distinguer les types.</span><span class="sxs-lookup"><span data-stu-id="f47fb-114">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="f47fb-115">Chaîne GUID qui identifie le type UDT spécifique dans la bibliothèque de types inscrite.</span><span class="sxs-lookup"><span data-stu-id="f47fb-115">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="f47fb-116">Chaîne GUID qui identifie la bibliothèque de types inscrite définissant le type.</span><span class="sxs-lookup"><span data-stu-id="f47fb-116">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="f47fb-117">Chaîne qui identifie la version de la bibliothèque de types définissant le type.</span><span class="sxs-lookup"><span data-stu-id="f47fb-117">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f47fb-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f47fb-118">Child Elements</span></span>  
 <span data-ttu-id="f47fb-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f47fb-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f47fb-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f47fb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f47fb-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f47fb-121">Element</span></span>|<span data-ttu-id="f47fb-122">Description</span><span class="sxs-lookup"><span data-stu-id="f47fb-122">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="f47fb-123">Collection d'éléments `userDefinedType`.</span><span class="sxs-lookup"><span data-stu-id="f47fb-123">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f47fb-124">Notes</span><span class="sxs-lookup"><span data-stu-id="f47fb-124">Remarks</span></span>  
 <span data-ttu-id="f47fb-125">Le runtime d'intégration COM+ crée des services en inspectant la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="f47fb-125">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="f47fb-126">Lorsqu'un composant COM+ contient des méthodes qui passent un VARIANT, le système ne peut pas déterminer les types réels à passer avant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f47fb-126">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="f47fb-127">Par conséquent, le passage d'un UDT dans un VARIANT échoue car ce n'est pas un type connu pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="f47fb-127">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="f47fb-128">Pour contourner ce problème, vous pouvez ajouter les UDT au fichier de configuration afin qu'ils puissent être inclus comme types connus sur le contrat de service approprié.</span><span class="sxs-lookup"><span data-stu-id="f47fb-128">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="f47fb-129">Pour ce faire, vous devez identifier de manière unique l'UDT et le ou les contrats, autrement dit, le ou les interfaces COM d'origine qui les utilisent.</span><span class="sxs-lookup"><span data-stu-id="f47fb-129">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="f47fb-130">L’exemple suivant illustre l’ajout de deux UDT spécifiques à`userDefinedTypes`la section < > du fichier de configuration à cet effet.</span><span class="sxs-lookup"><span data-stu-id="f47fb-130">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <userDefinedTypes>
      <userDefinedType name="CustomerType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">
      </userDefinedType>
      <userDefinedType name="AddressType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">
      </userDefinedType>
    </userDefinedTypes>
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="f47fb-131">Lorsque le service est initialisé, le runtime d'intégration recherche les types spécifiés et les ajoute à la collection de types connus pour les contrats spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f47fb-131">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47fb-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f47fb-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [<span data-ttu-id="f47fb-133">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="f47fb-133">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="f47fb-134">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="f47fb-134">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="f47fb-135">Guide pratique : Configurer les paramètres du service COM+</span><span class="sxs-lookup"><span data-stu-id="f47fb-135">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
