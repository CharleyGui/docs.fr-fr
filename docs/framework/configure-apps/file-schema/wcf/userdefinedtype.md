---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854834"
---
# <a name="userdefinedtype"></a><span data-ttu-id="a03a7-101">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="a03a7-101">\<userDefinedType></span></span>
<span data-ttu-id="a03a7-102">Représente un type défini par l'utilisateur (UDT) à inclure dans le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="a03a7-102">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
<span data-ttu-id="a03a7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a03a7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a03a7-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a03a7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a03a7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comconventions**](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="a03a7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="a03a7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="a03a7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="a03a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<userDefinedTypes >** ](userdefinedtypes.md)</span><span class="sxs-lookup"><span data-stu-id="a03a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)</span></span>\
<span data-ttu-id="a03a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userDefinedType >**</span><span class="sxs-lookup"><span data-stu-id="a03a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a03a7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a03a7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a03a7-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a03a7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a03a7-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a03a7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a03a7-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a03a7-112">Attributes</span></span>  
  
|<span data-ttu-id="a03a7-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="a03a7-113">Attribute</span></span>|<span data-ttu-id="a03a7-114">Description</span><span class="sxs-lookup"><span data-stu-id="a03a7-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a03a7-115">Attribut facultatif qui contient une chaîne fournissant le nom de type lisible.</span><span class="sxs-lookup"><span data-stu-id="a03a7-115">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="a03a7-116">Il n'est pas utilisé par l'exécution mais aide le lecteur à distinguer les types.</span><span class="sxs-lookup"><span data-stu-id="a03a7-116">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="a03a7-117">Chaîne GUID qui identifie le type UDT spécifique dans la bibliothèque de types inscrite.</span><span class="sxs-lookup"><span data-stu-id="a03a7-117">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="a03a7-118">Chaîne GUID qui identifie la bibliothèque de types inscrite définissant le type.</span><span class="sxs-lookup"><span data-stu-id="a03a7-118">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="a03a7-119">Chaîne qui identifie la version de la bibliothèque de types définissant le type.</span><span class="sxs-lookup"><span data-stu-id="a03a7-119">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a03a7-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a03a7-120">Child Elements</span></span>  
 <span data-ttu-id="a03a7-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a03a7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a03a7-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a03a7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a03a7-123">Élément</span><span class="sxs-lookup"><span data-stu-id="a03a7-123">Element</span></span>|<span data-ttu-id="a03a7-124">Description</span><span class="sxs-lookup"><span data-stu-id="a03a7-124">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="a03a7-125">Collection d'éléments `userDefinedType`.</span><span class="sxs-lookup"><span data-stu-id="a03a7-125">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a03a7-126">Notes</span><span class="sxs-lookup"><span data-stu-id="a03a7-126">Remarks</span></span>  
 <span data-ttu-id="a03a7-127">Le runtime d'intégration COM+ crée des services en inspectant la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="a03a7-127">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="a03a7-128">Lorsqu'un composant COM+ contient des méthodes qui passent un VARIANT, le système ne peut pas déterminer les types réels à passer avant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a03a7-128">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="a03a7-129">Par conséquent, le passage d'un UDT dans un VARIANT échoue car ce n'est pas un type connu pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="a03a7-129">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="a03a7-130">Pour contourner ce problème, vous pouvez ajouter les UDT au fichier de configuration afin qu'ils puissent être inclus comme types connus sur le contrat de service approprié.</span><span class="sxs-lookup"><span data-stu-id="a03a7-130">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="a03a7-131">Pour ce faire, vous devez identifier de manière unique l'UDT et le ou les contrats, autrement dit, le ou les interfaces COM d'origine qui les utilisent.</span><span class="sxs-lookup"><span data-stu-id="a03a7-131">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="a03a7-132">L’exemple suivant illustre l’ajout de deux UDT spécifiques à`userDefinedTypes`la section < > du fichier de configuration à cet effet.</span><span class="sxs-lookup"><span data-stu-id="a03a7-132">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
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
  
 <span data-ttu-id="a03a7-133">Lorsque le service est initialisé, le runtime d'intégration recherche les types spécifiés et les ajoute à la collection de types connus pour les contrats spécifiés.</span><span class="sxs-lookup"><span data-stu-id="a03a7-133">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03a7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a03a7-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [<span data-ttu-id="a03a7-135">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="a03a7-135">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="a03a7-136">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="a03a7-136">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a03a7-137">Guide pratique pour Configurer les paramètres du service COM+</span><span class="sxs-lookup"><span data-stu-id="a03a7-137">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
