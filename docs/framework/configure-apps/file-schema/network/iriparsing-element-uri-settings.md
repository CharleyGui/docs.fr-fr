---
title: <iriParsing>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698090"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="2d7d5-102">\<élément iriParsing > (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="2d7d5-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="2d7d5-103">Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[<span data-ttu-id="2d7d5-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2d7d5-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2d7d5-105">&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2d7d5-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="2d7d5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<IriParsing** ></span><span class="sxs-lookup"><span data-stu-id="2d7d5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d7d5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d7d5-107">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d7d5-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2d7d5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2d7d5-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d7d5-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="2d7d5-110">Attributes</span></span>  
  
|<span data-ttu-id="2d7d5-111">**Élément**</span><span class="sxs-lookup"><span data-stu-id="2d7d5-111">**Element**</span></span>|<span data-ttu-id="2d7d5-112">**Description**</span><span class="sxs-lookup"><span data-stu-id="2d7d5-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="2d7d5-113">Spécifie si l’analyse IRI est activée.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-113">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="2d7d5-114">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d7d5-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2d7d5-115">Child Elements</span></span>  
 <span data-ttu-id="2d7d5-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="2d7d5-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d7d5-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2d7d5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2d7d5-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="2d7d5-118">**Element**</span></span>|<span data-ttu-id="2d7d5-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="2d7d5-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2d7d5-120">URI</span><span class="sxs-lookup"><span data-stu-id="2d7d5-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="2d7d5-121">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="2d7d5-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d7d5-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="2d7d5-122">Remarks</span></span>  
 <span data-ttu-id="2d7d5-123">La classe de <xref:System.Uri> existante a été étendue dans .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="2d7d5-124">3,0 SP1 et 2,0 SP1 pour assurer la prise en charge des IRI (International Resource Identifier) et des noms de domaine internationaux (IDN).</span><span class="sxs-lookup"><span data-stu-id="2d7d5-124">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="2d7d5-125">Les utilisateurs actuels ne voient aucune modification du comportement .NET Framework 2,0, sauf s’ils activent spécifiquement la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="2d7d5-126">Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2d7d5-127">Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="2d7d5-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="2d7d5-128">Ajoutez la ligne suivante au fichier machine. config dans le répertoire .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="2d7d5-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="2d7d5-129">Spécifie si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-129">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="2d7d5-130">Cela est spécifié dans le fichier machine.config ou app.config.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="2d7d5-131">L’activation de l’analyse IRI (iriParsing enabled = `true`) effectue la normalisation et la vérification des caractères selon les dernières règles IRI de la norme RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-131">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="2d7d5-132">La valeur par défaut est `false` et effectue la normalisation et la vérification des caractères conformément aux RFC 2396 et RFC 3986 (pour les littéraux IPv6).</span><span class="sxs-lookup"><span data-stu-id="2d7d5-132">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="2d7d5-133">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="2d7d5-133">Configuration Files</span></span>  
 <span data-ttu-id="2d7d5-134">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2d7d5-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d7d5-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="2d7d5-135">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2d7d5-136">Description</span><span class="sxs-lookup"><span data-stu-id="2d7d5-136">Description</span></span>  
 <span data-ttu-id="2d7d5-137">L’exemple suivant illustre une configuration utilisée par la classe <xref:System.Uri> pour prendre en charge l’analyse des IRI et les noms IDN.</span><span class="sxs-lookup"><span data-stu-id="2d7d5-137">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2d7d5-138">Code</span><span class="sxs-lookup"><span data-stu-id="2d7d5-138">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d7d5-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d7d5-139">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="2d7d5-140">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="2d7d5-140">Network Settings Schema</span></span>](index.md)
