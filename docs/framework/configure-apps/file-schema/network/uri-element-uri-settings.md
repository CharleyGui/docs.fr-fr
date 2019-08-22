---
title: <Uri>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 80d71da5ca680872e4948fa8ff135fbbdf08cffe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663963"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="5ca11-102">\<URI >, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="5ca11-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="5ca11-103">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="5ca11-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="5ca11-104">Hiérarchie de schéma</span><span class="sxs-lookup"><span data-stu-id="5ca11-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="5ca11-105">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="5ca11-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="5ca11-106">\<uri></span><span class="sxs-lookup"><span data-stu-id="5ca11-106">\<uri></span></span>](uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="5ca11-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ca11-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ca11-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5ca11-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5ca11-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5ca11-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ca11-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5ca11-110">Attributes</span></span>  
 <span data-ttu-id="5ca11-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5ca11-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ca11-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5ca11-112">Child Elements</span></span>  
  
|<span data-ttu-id="5ca11-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="5ca11-113">**Element**</span></span>|<span data-ttu-id="5ca11-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="5ca11-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5ca11-115">idn</span><span class="sxs-lookup"><span data-stu-id="5ca11-115">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="5ca11-116">Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="5ca11-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="5ca11-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="5ca11-117">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="5ca11-118">Spécifie si l’analyse IRI (International Resource Identifier) est appliquée <xref:System.Uri> et si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="5ca11-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="5ca11-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="5ca11-119">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="5ca11-120">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="5ca11-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ca11-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5ca11-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5ca11-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="5ca11-122">**Element**</span></span>|<span data-ttu-id="5ca11-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="5ca11-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5ca11-124">configuration</span><span class="sxs-lookup"><span data-stu-id="5ca11-124">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="5ca11-125">Contient les paramètres de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="5ca11-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ca11-126">Notes</span><span class="sxs-lookup"><span data-stu-id="5ca11-126">Remarks</span></span>  
 <span data-ttu-id="5ca11-127">L' `uri` élément contient des paramètres pour les membres <xref:System.Uri> de la classe utilisée par les <xref:System.Net> classes de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5ca11-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="5ca11-128">Les paramètres configurent la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="5ca11-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ca11-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="5ca11-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5ca11-130">Description</span><span class="sxs-lookup"><span data-stu-id="5ca11-130">Description</span></span>  
 <span data-ttu-id="5ca11-131">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse des IRI et les noms IDN.</span><span class="sxs-lookup"><span data-stu-id="5ca11-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="5ca11-132">L’exemple efface également tous les paramètres de schéma, puis ajoute la prise en charge pour ne pas échapper les délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="5ca11-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5ca11-133">Code</span><span class="sxs-lookup"><span data-stu-id="5ca11-133">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ca11-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ca11-134">See also</span></span>

- [<span data-ttu-id="5ca11-135">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="5ca11-135">Network Settings Schema</span></span>](index.md)
