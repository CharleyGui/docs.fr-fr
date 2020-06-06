---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152578"
---
# \<serviceTokenResolver>
<span data-ttu-id="a5d35-101">Inscrit le programme de résolution de jetons de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="a5d35-101">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a5d35-102">Le programme de résolution de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="a5d35-102">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="a5d35-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5d35-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5d35-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a5d35-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a5d35-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a5d35-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5d35-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="a5d35-106">Attributes</span></span>  
  
|<span data-ttu-id="a5d35-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="a5d35-107">Attribute</span></span>|<span data-ttu-id="a5d35-108">Description</span><span class="sxs-lookup"><span data-stu-id="a5d35-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5d35-109">type</span><span class="sxs-lookup"><span data-stu-id="a5d35-109">type</span></span>|<span data-ttu-id="a5d35-110">Spécifie le type du programme de résolution de jetons de service.</span><span class="sxs-lookup"><span data-stu-id="a5d35-110">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="a5d35-111">Le <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type ou un type qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="a5d35-111">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="a5d35-112">Pour plus d’informations sur la spécification de l' `type` attribut, consultez [références de types personnalisés].</span><span class="sxs-lookup"><span data-stu-id="a5d35-112">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="a5d35-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="a5d35-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5d35-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a5d35-114">Child Elements</span></span>  
 <span data-ttu-id="a5d35-115">Aucune</span><span class="sxs-lookup"><span data-stu-id="a5d35-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5d35-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a5d35-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a5d35-117">Élément</span><span class="sxs-lookup"><span data-stu-id="a5d35-117">Element</span></span>|<span data-ttu-id="a5d35-118">Description</span><span class="sxs-lookup"><span data-stu-id="a5d35-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a5d35-119">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a5d35-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5d35-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="a5d35-120">Remarks</span></span>  
 <span data-ttu-id="a5d35-121">Le programme de résolution de jetons de service peut être utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="a5d35-121">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="a5d35-122">Il est utilisé pour récupérer la clé qui doit être utilisée pour déchiffrer les jetons entrants.</span><span class="sxs-lookup"><span data-stu-id="a5d35-122">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="a5d35-123">Vous devez spécifier l' `type` attribut.</span><span class="sxs-lookup"><span data-stu-id="a5d35-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="a5d35-124">Le type spécifié peut être <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou un type personnalisé qui dérive de la <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="a5d35-124">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="a5d35-125">Certains gestionnaires de jetons vous permettent de spécifier des paramètres de résolution de jetons de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a5d35-125">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="a5d35-126">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés dans la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a5d35-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5d35-127">La spécification de l' `<serviceTokenResolver>` élément en tant qu’élément enfant de l' [\<identityConfiguration>](identityconfiguration.md) élément a été dépréciée, mais est toujours prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="a5d35-127">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="a5d35-128">Les paramètres de l' `<securityTokenHandlerConfiguration>` élément remplacent ceux de l' `<identityConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="a5d35-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5d35-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5d35-129">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
