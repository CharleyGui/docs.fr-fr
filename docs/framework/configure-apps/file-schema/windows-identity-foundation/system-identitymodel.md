---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251791"
---
# \<system.identityModel>
<span data-ttu-id="3d2c6-102">Fournit la configuration permettant d’activer les options de Windows Identity Foundation (WIF) dans les applications.</span><span class="sxs-lookup"><span data-stu-id="3d2c6-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="3d2c6-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d2c6-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d2c6-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3d2c6-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3d2c6-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3d2c6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d2c6-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="3d2c6-106">Attributes</span></span>  
 <span data-ttu-id="3d2c6-107">Aucune</span><span class="sxs-lookup"><span data-stu-id="3d2c6-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3d2c6-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3d2c6-108">Child Elements</span></span>  
  
|<span data-ttu-id="3d2c6-109">Élément</span><span class="sxs-lookup"><span data-stu-id="3d2c6-109">Element</span></span>|<span data-ttu-id="3d2c6-110">Description</span><span class="sxs-lookup"><span data-stu-id="3d2c6-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="3d2c6-111">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="3d2c6-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d2c6-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3d2c6-112">Parent Elements</span></span>  
  
|<span data-ttu-id="3d2c6-113">Élément</span><span class="sxs-lookup"><span data-stu-id="3d2c6-113">Element</span></span>|<span data-ttu-id="3d2c6-114">Description</span><span class="sxs-lookup"><span data-stu-id="3d2c6-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="3d2c6-115">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3d2c6-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d2c6-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="3d2c6-116">Remarks</span></span>  
 <span data-ttu-id="3d2c6-117">Ajoutez une `<system.identityModel>` section au fichier de configuration pour configurer un service ou une application pour utiliser Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="3d2c6-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="3d2c6-118">L' `<system.identityModel>` élément est représenté par la <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> classe.</span><span class="sxs-lookup"><span data-stu-id="3d2c6-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d2c6-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="3d2c6-119">Example</span></span>  
 <span data-ttu-id="3d2c6-120">L’exemple suivant montre comment ajouter une `<system.identityModel>` section à un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="3d2c6-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="3d2c6-121">Vous devez d’abord ajouter la section de configuration et la déclaration d’espace de noms sous l' `<configSections>` élément.</span><span class="sxs-lookup"><span data-stu-id="3d2c6-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="3d2c6-122">Vous pouvez ensuite ajouter l' `<system.IdentityModel>` élément à votre fichier de configuration pour spécifier une ou plusieurs configurations d’identité.</span><span class="sxs-lookup"><span data-stu-id="3d2c6-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d2c6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d2c6-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
