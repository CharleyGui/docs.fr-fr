---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 216b4c73e06469d6577c61338ad1af0fdd2dc05e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185572"
---
# \<system.identityModel>

<span data-ttu-id="63c18-102">Fournit la configuration permettant d’activer les options de Windows Identity Foundation (WIF) dans les applications.</span><span class="sxs-lookup"><span data-stu-id="63c18-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="63c18-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63c18-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63c18-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="63c18-104">Attributes and Elements</span></span>  

 <span data-ttu-id="63c18-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="63c18-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63c18-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="63c18-106">Attributes</span></span>  

 <span data-ttu-id="63c18-107">None</span><span class="sxs-lookup"><span data-stu-id="63c18-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63c18-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="63c18-108">Child Elements</span></span>  
  
|<span data-ttu-id="63c18-109">Élément</span><span class="sxs-lookup"><span data-stu-id="63c18-109">Element</span></span>|<span data-ttu-id="63c18-110">Description</span><span class="sxs-lookup"><span data-stu-id="63c18-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="63c18-111">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="63c18-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63c18-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="63c18-112">Parent Elements</span></span>  
  
|<span data-ttu-id="63c18-113">Élément</span><span class="sxs-lookup"><span data-stu-id="63c18-113">Element</span></span>|<span data-ttu-id="63c18-114">Description</span><span class="sxs-lookup"><span data-stu-id="63c18-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="63c18-115">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63c18-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63c18-116">Notes</span><span class="sxs-lookup"><span data-stu-id="63c18-116">Remarks</span></span>  

 <span data-ttu-id="63c18-117">Ajoutez une `<system.identityModel>` section au fichier de configuration pour configurer un service ou une application pour utiliser Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="63c18-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="63c18-118">L' `<system.identityModel>` élément est représenté par la <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> classe.</span><span class="sxs-lookup"><span data-stu-id="63c18-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63c18-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="63c18-119">Example</span></span>  

 <span data-ttu-id="63c18-120">L’exemple suivant montre comment ajouter une `<system.identityModel>` section à un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="63c18-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="63c18-121">Vous devez d’abord ajouter la section de configuration et la déclaration d’espace de noms sous l' `<configSections>` élément.</span><span class="sxs-lookup"><span data-stu-id="63c18-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="63c18-122">Vous pouvez ensuite ajouter l' `<system.IdentityModel>` élément à votre fichier de configuration pour spécifier une ou plusieurs configurations d’identité.</span><span class="sxs-lookup"><span data-stu-id="63c18-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63c18-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63c18-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
