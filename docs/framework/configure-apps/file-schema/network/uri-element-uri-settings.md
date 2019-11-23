---
title: <uri>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697436"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="6f584-102">\<URI >, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="6f584-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="6f584-103">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="6f584-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[<span data-ttu-id="6f584-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="6f584-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6f584-105">&nbsp;&nbsp; **\<uri >**</span><span class="sxs-lookup"><span data-stu-id="6f584-105">&nbsp;&nbsp;**\<uri>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f584-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f584-106">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f584-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6f584-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6f584-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6f584-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f584-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6f584-109">Attributes</span></span>  
 <span data-ttu-id="6f584-110">Aucune.</span><span class="sxs-lookup"><span data-stu-id="6f584-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f584-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6f584-111">Child Elements</span></span>  
  
|<span data-ttu-id="6f584-112">**Élément**</span><span class="sxs-lookup"><span data-stu-id="6f584-112">**Element**</span></span>|<span data-ttu-id="6f584-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="6f584-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6f584-114">idn</span><span class="sxs-lookup"><span data-stu-id="6f584-114">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="6f584-115">Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="6f584-115">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="6f584-116">iriParsing</span><span class="sxs-lookup"><span data-stu-id="6f584-116">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="6f584-117">Spécifie si l’analyse IRI (International Resource Identifier) est appliquée à <xref:System.Uri> et si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="6f584-117">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="6f584-118">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="6f584-118">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="6f584-119">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="6f584-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f584-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6f584-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6f584-121">**Élément**</span><span class="sxs-lookup"><span data-stu-id="6f584-121">**Element**</span></span>|<span data-ttu-id="6f584-122">**Description**</span><span class="sxs-lookup"><span data-stu-id="6f584-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6f584-123">configuration</span><span class="sxs-lookup"><span data-stu-id="6f584-123">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="6f584-124">Contient les paramètres de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="6f584-124">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f584-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="6f584-125">Remarks</span></span>  
 <span data-ttu-id="6f584-126">L’élément `uri` contient des paramètres pour les membres de la classe <xref:System.Uri> utilisée par les classes de l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="6f584-126">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="6f584-127">Les paramètres configurent la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="6f584-127">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f584-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f584-128">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6f584-129">Description</span><span class="sxs-lookup"><span data-stu-id="6f584-129">Description</span></span>  
 <span data-ttu-id="6f584-130">L’exemple suivant illustre une configuration utilisée par la classe <xref:System.Uri> pour prendre en charge l’analyse des IRI et les noms IDN.</span><span class="sxs-lookup"><span data-stu-id="6f584-130">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="6f584-131">L’exemple efface également tous les paramètres de schéma, puis ajoute la prise en charge pour ne pas échapper les délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="6f584-131">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6f584-132">Code</span><span class="sxs-lookup"><span data-stu-id="6f584-132">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f584-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f584-133">See also</span></span>

- [<span data-ttu-id="6f584-134">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="6f584-134">Network Settings Schema</span></span>](index.md)
