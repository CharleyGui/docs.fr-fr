---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251926"
---
# \<remove>
<span data-ttu-id="6b118-101">Supprime le gestionnaire de jetons de sécurité spécifié de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="6b118-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="6b118-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b118-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b118-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6b118-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6b118-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6b118-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b118-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="6b118-105">Attributes</span></span>  
  
|<span data-ttu-id="6b118-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="6b118-106">Attribute</span></span>|<span data-ttu-id="6b118-107">Description</span><span class="sxs-lookup"><span data-stu-id="6b118-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b118-108">type</span><span class="sxs-lookup"><span data-stu-id="6b118-108">type</span></span>|<span data-ttu-id="6b118-109">Nom de type CLR du gestionnaire de jetons à supprimer.</span><span class="sxs-lookup"><span data-stu-id="6b118-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="6b118-110">Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="6b118-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="6b118-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6b118-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b118-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6b118-112">Child Elements</span></span>  
 <span data-ttu-id="6b118-113">Aucune</span><span class="sxs-lookup"><span data-stu-id="6b118-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b118-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6b118-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6b118-115">Élément</span><span class="sxs-lookup"><span data-stu-id="6b118-115">Element</span></span>|<span data-ttu-id="6b118-116">Description</span><span class="sxs-lookup"><span data-stu-id="6b118-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="6b118-117">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6b118-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b118-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b118-118">Example</span></span>  
 <span data-ttu-id="6b118-119">Le code XML suivant montre l’utilisation des `<add>` `<remove>` éléments et pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6b118-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="6b118-120">Le code XML est extrait de l' `ClaimsAwareWebFarm` exemple.</span><span class="sxs-lookup"><span data-stu-id="6b118-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
