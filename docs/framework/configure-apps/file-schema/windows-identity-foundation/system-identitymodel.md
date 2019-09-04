---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251791"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="746fb-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="746fb-102">\<system.identityModel></span></span>
<span data-ttu-id="746fb-103">Fournit la configuration permettant d’activer les options de Windows Identity Foundation (WIF) dans les applications.</span><span class="sxs-lookup"><span data-stu-id="746fb-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
<span data-ttu-id="746fb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="746fb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="746fb-105">&nbsp;&nbsp; **\<System. identityModel >**</span><span class="sxs-lookup"><span data-stu-id="746fb-105">&nbsp;&nbsp;**\<system.identityModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="746fb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="746fb-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="746fb-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="746fb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="746fb-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="746fb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="746fb-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="746fb-109">Attributes</span></span>  
 <span data-ttu-id="746fb-110">Aucun</span><span class="sxs-lookup"><span data-stu-id="746fb-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="746fb-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="746fb-111">Child Elements</span></span>  
  
|<span data-ttu-id="746fb-112">Élément</span><span class="sxs-lookup"><span data-stu-id="746fb-112">Element</span></span>|<span data-ttu-id="746fb-113">Description</span><span class="sxs-lookup"><span data-stu-id="746fb-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="746fb-114">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="746fb-114">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="746fb-115">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="746fb-115">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="746fb-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="746fb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="746fb-117">Élément</span><span class="sxs-lookup"><span data-stu-id="746fb-117">Element</span></span>|<span data-ttu-id="746fb-118">Description</span><span class="sxs-lookup"><span data-stu-id="746fb-118">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="746fb-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="746fb-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="746fb-120">Notes</span><span class="sxs-lookup"><span data-stu-id="746fb-120">Remarks</span></span>  
 <span data-ttu-id="746fb-121">Ajoutez une `<system.identityModel>` section au fichier de configuration pour configurer un service ou une application pour utiliser Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="746fb-121">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="746fb-122">L' `<system.identityModel>` élément est représenté par la <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> classe.</span><span class="sxs-lookup"><span data-stu-id="746fb-122">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="746fb-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="746fb-123">Example</span></span>  
 <span data-ttu-id="746fb-124">L’exemple suivant montre comment ajouter une `<system.identityModel>` section à un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="746fb-124">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="746fb-125">Vous devez d’abord ajouter la section de configuration et la Déclaration `<configSections>` d’espace de noms sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="746fb-125">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="746fb-126">Vous pouvez ensuite ajouter l' `<system.IdentityModel>` élément à votre fichier de configuration pour spécifier une ou plusieurs configurations d’identité.</span><span class="sxs-lookup"><span data-stu-id="746fb-126">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="746fb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="746fb-127">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
