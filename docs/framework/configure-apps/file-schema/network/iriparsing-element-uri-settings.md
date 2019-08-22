---
title: <iriParsing>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 2c99edf2f1a03e0e510858c106cad43b0eaa27b4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664084"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="c03ee-102">\<iriParsing >, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="c03ee-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="c03ee-103">Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="c03ee-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="c03ee-104">Hiérarchie de schéma</span><span class="sxs-lookup"><span data-stu-id="c03ee-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="c03ee-105">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="c03ee-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="c03ee-106">\<URI >, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="c03ee-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="c03ee-107">\<iriParsing></span><span class="sxs-lookup"><span data-stu-id="c03ee-107">\<iriParsing></span></span>](iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="c03ee-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c03ee-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c03ee-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c03ee-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c03ee-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c03ee-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c03ee-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="c03ee-111">Attributes</span></span>  
  
|<span data-ttu-id="c03ee-112">**Élément**</span><span class="sxs-lookup"><span data-stu-id="c03ee-112">**Element**</span></span>|<span data-ttu-id="c03ee-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="c03ee-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="c03ee-114">Spécifie si l’analyse IRI est activée.</span><span class="sxs-lookup"><span data-stu-id="c03ee-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="c03ee-115">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="c03ee-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c03ee-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c03ee-116">Child Elements</span></span>  
 <span data-ttu-id="c03ee-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="c03ee-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c03ee-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c03ee-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c03ee-119">**Élément**</span><span class="sxs-lookup"><span data-stu-id="c03ee-119">**Element**</span></span>|<span data-ttu-id="c03ee-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="c03ee-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c03ee-121">URI</span><span class="sxs-lookup"><span data-stu-id="c03ee-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="c03ee-122">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="c03ee-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c03ee-123">Notes</span><span class="sxs-lookup"><span data-stu-id="c03ee-123">Remarks</span></span>  
 <span data-ttu-id="c03ee-124">La classe <xref:System.Uri> existante a été étendue dans .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="c03ee-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="c03ee-125">3,0 SP1 et 2,0 SP1 pour assurer la prise en charge des IRI (International Resource Identifier) et des noms de domaine internationaux (IDN).</span><span class="sxs-lookup"><span data-stu-id="c03ee-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="c03ee-126">Les utilisateurs actuels ne voient aucune modification du comportement .NET Framework 2,0, sauf s’ils activent spécifiquement la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="c03ee-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="c03ee-127">Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c03ee-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c03ee-128">Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises:</span><span class="sxs-lookup"><span data-stu-id="c03ee-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="c03ee-129">Ajoutez la ligne suivante au fichier machine. config dans le répertoire .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="c03ee-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="c03ee-130">Spécifie si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="c03ee-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="c03ee-131">Cela est spécifié dans le fichier machine.config ou app.config.</span><span class="sxs-lookup"><span data-stu-id="c03ee-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="c03ee-132">L’activation de l’analyse IRI (iriParsing `true`Enabled =) effectue la normalisation et la vérification des caractères selon les dernières règles IRI de la norme RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="c03ee-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="c03ee-133">La valeur par défaut `false` est et effectue la normalisation et la vérification des caractères selon les spécifications RFC 2396 et RFC 3986 (pour les littéraux IPv6).</span><span class="sxs-lookup"><span data-stu-id="c03ee-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="c03ee-134">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="c03ee-134">Configuration Files</span></span>  
 <span data-ttu-id="c03ee-135">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c03ee-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c03ee-136">Exemples</span><span class="sxs-lookup"><span data-stu-id="c03ee-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c03ee-137">Description</span><span class="sxs-lookup"><span data-stu-id="c03ee-137">Description</span></span>  
 <span data-ttu-id="c03ee-138">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse des IRI et les noms IDN.</span><span class="sxs-lookup"><span data-stu-id="c03ee-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c03ee-139">Code</span><span class="sxs-lookup"><span data-stu-id="c03ee-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c03ee-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c03ee-140">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="c03ee-141">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="c03ee-141">Network Settings Schema</span></span>](index.md)
