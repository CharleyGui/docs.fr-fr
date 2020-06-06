---
title: <add>, élément de webRequestModules (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155022"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="4fe17-102">\<add>, élément de webRequestModules (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="4fe17-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="4fe17-103">Ajoute un module de demande Web personnalisé à l’application.</span><span class="sxs-lookup"><span data-stu-id="4fe17-103">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="4fe17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fe17-104">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe17-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4fe17-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4fe17-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4fe17-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe17-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="4fe17-107">Attributes</span></span>  
  
|<span data-ttu-id="4fe17-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="4fe17-108">**Attribute**</span></span>|<span data-ttu-id="4fe17-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="4fe17-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="4fe17-110">Préfixe URI pour les requêtes gérées par ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="4fe17-110">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="4fe17-111">Nom de type qualifié complet (indiqué par la <xref:System.Type.FullName%2A> propriété) et nom de l’assembly (indiqué par la <xref:System.Reflection.Assembly.FullName%2A> propriété), séparés par une virgule, qui implémente ce module de demande Web.</span><span class="sxs-lookup"><span data-stu-id="4fe17-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fe17-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4fe17-112">Child Elements</span></span>  
 <span data-ttu-id="4fe17-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4fe17-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe17-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4fe17-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe17-115">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="4fe17-115">**Element**</span></span>|<span data-ttu-id="4fe17-116">**Description**</span><span class="sxs-lookup"><span data-stu-id="4fe17-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4fe17-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="4fe17-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="4fe17-118">Spécifie les modules à utiliser pour demander des informations à des hôtes réseau.</span><span class="sxs-lookup"><span data-stu-id="4fe17-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe17-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="4fe17-119">Remarks</span></span>  
 <span data-ttu-id="4fe17-120">L' `prefix` attribut définit le préfixe URI qui utilise le module de demande Web spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fe17-120">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="4fe17-121">Les modules de demande Web sont généralement enregistrés pour gérer un protocole spécifique, tel que HTTP ou FTP, mais peuvent être inscrits pour gérer une demande à un serveur ou à un chemin d’accès spécifique sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="4fe17-121">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="4fe17-122">Le module de demande Web est créé lorsqu’un préfixe d’URI correspondant est passé à la <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="4fe17-122">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="4fe17-123">La valeur de l' `prefix` attribut doit être les caractères de début d’un URI valide.</span><span class="sxs-lookup"><span data-stu-id="4fe17-123">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="4fe17-124">Par exemple, `http` ou `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="4fe17-124">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="4fe17-125">La valeur de l' `type` attribut doit être un nom de type valide et le nom d’assembly correspondant, séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="4fe17-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="4fe17-126">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="4fe17-126">Configuration Files</span></span>  
 <span data-ttu-id="4fe17-127">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4fe17-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe17-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="4fe17-128">Example</span></span>  
 <span data-ttu-id="4fe17-129">L’exemple suivant inscrit un module de demande Web personnalisé pour HTTP.</span><span class="sxs-lookup"><span data-stu-id="4fe17-129">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="4fe17-130">Vous devez remplacer les valeurs de version et PublicKeyToken par les valeurs correctes pour le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fe17-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fe17-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fe17-131">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="4fe17-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="4fe17-132">Network Settings Schema</span></span>](index.md)
