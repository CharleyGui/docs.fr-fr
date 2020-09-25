---
title: <uri>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 2f22d70407d10dbb38f0cb8d3a8ac74ff3fe8763
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190200"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="9ea6a-102">\<uri>, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="9ea6a-102">\<uri> Element (Uri Settings)</span></span>

<span data-ttu-id="9ea6a-103">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="9ea6a-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="9ea6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ea6a-104">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ea6a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9ea6a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9ea6a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ea6a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="9ea6a-107">Attributes</span></span>  

 <span data-ttu-id="9ea6a-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ea6a-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9ea6a-109">Child Elements</span></span>  
  
|<span data-ttu-id="9ea6a-110">**Element**</span><span class="sxs-lookup"><span data-stu-id="9ea6a-110">**Element**</span></span>|<span data-ttu-id="9ea6a-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="9ea6a-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9ea6a-112">IDN</span><span class="sxs-lookup"><span data-stu-id="9ea6a-112">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="9ea6a-113">Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="9ea6a-114">iriParsing</span><span class="sxs-lookup"><span data-stu-id="9ea6a-114">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="9ea6a-115">Spécifie si l’analyse IRI (International Resource Identifier) est appliquée <xref:System.Uri> et si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-115">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="9ea6a-116">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="9ea6a-116">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="9ea6a-117">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-117">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ea6a-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9ea6a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9ea6a-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="9ea6a-119">**Element**</span></span>|<span data-ttu-id="9ea6a-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="9ea6a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9ea6a-121">configuration</span><span class="sxs-lookup"><span data-stu-id="9ea6a-121">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="9ea6a-122">Contient les paramètres de tous les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-122">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ea6a-123">Notes</span><span class="sxs-lookup"><span data-stu-id="9ea6a-123">Remarks</span></span>  

 <span data-ttu-id="9ea6a-124">L' `uri` élément contient des paramètres pour les membres de la <xref:System.Uri> classe utilisée par les classes de l' <xref:System.Net> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-124">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="9ea6a-125">Les paramètres configurent la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-125">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ea6a-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ea6a-126">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9ea6a-127">Description</span><span class="sxs-lookup"><span data-stu-id="9ea6a-127">Description</span></span>  

 <span data-ttu-id="9ea6a-128">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse des IRI et les noms IDN.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-128">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="9ea6a-129">L’exemple efface également tous les paramètres de schéma, puis ajoute la prise en charge pour ne pas échapper les délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="9ea6a-129">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9ea6a-130">Code</span><span class="sxs-lookup"><span data-stu-id="9ea6a-130">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ea6a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ea6a-131">See also</span></span>

- [<span data-ttu-id="9ea6a-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="9ea6a-132">Network Settings Schema</span></span>](index.md)
