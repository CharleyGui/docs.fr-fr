---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 11aeed0277fc13cbd9a65232311bd575a4a81ff7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942584"
---
# <a name="remove"></a><span data-ttu-id="d1da4-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="d1da4-101">\<remove></span></span>
<span data-ttu-id="d1da4-102">Supprime le gestionnaire de jetons de sécurité spécifié de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="d1da4-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="d1da4-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d1da4-103">\<system.identityModel></span></span>  
<span data-ttu-id="d1da4-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d1da4-104">\<identityConfiguration></span></span>  
<span data-ttu-id="d1da4-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d1da4-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d1da4-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="d1da4-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1da4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1da4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1da4-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d1da4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1da4-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d1da4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1da4-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d1da4-110">Attributes</span></span>  
  
|<span data-ttu-id="d1da4-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="d1da4-111">Attribute</span></span>|<span data-ttu-id="d1da4-112">Description</span><span class="sxs-lookup"><span data-stu-id="d1da4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1da4-113">type</span><span class="sxs-lookup"><span data-stu-id="d1da4-113">type</span></span>|<span data-ttu-id="d1da4-114">Nom de type CLR du gestionnaire de jetons à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d1da4-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="d1da4-115">Pour plus d’informations sur la spécification de `type` l’attribut, consultez [références de types personnalisés](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="d1da4-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="d1da4-116">Requis.</span><span class="sxs-lookup"><span data-stu-id="d1da4-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1da4-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1da4-117">Child Elements</span></span>  
 <span data-ttu-id="d1da4-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="d1da4-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1da4-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1da4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d1da4-120">Élément</span><span class="sxs-lookup"><span data-stu-id="d1da4-120">Element</span></span>|<span data-ttu-id="d1da4-121">Description</span><span class="sxs-lookup"><span data-stu-id="d1da4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1da4-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d1da4-122">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="d1da4-123">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d1da4-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1da4-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1da4-124">Example</span></span>  
 <span data-ttu-id="d1da4-125">Le code XML suivant montre l’utilisation des `<add>` éléments `<remove>` et pour remplacer le gestionnaire de jetons de session par défaut par un gestionnaire de jetons de session personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d1da4-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="d1da4-126">Le code XML est extrait de `ClaimsAwareWebFarm` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="d1da4-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
