---
title: <idn>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 5fe2eafee702be96bfdca80a06af4a040d9ef0f6
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664119"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="3e71f-102">\<Élément > IDN (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="3e71f-102">\<idn> Element (Uri Settings)</span></span>
<span data-ttu-id="3e71f-103">Spécifie si l’analyse des IDN (Internationalized Domain Name) est appliquée à un nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="3e71f-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="3e71f-104">Hiérarchie de schéma</span><span class="sxs-lookup"><span data-stu-id="3e71f-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="3e71f-105">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="3e71f-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="3e71f-106">\<URI >, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="3e71f-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="3e71f-107">\<idn></span><span class="sxs-lookup"><span data-stu-id="3e71f-107">\<idn></span></span>](idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="3e71f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e71f-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e71f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3e71f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3e71f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3e71f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e71f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="3e71f-111">Attributes</span></span>  
  
|<span data-ttu-id="3e71f-112">**Élément**</span><span class="sxs-lookup"><span data-stu-id="3e71f-112">**Element**</span></span>|<span data-ttu-id="3e71f-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="3e71f-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="3e71f-114">Spécifie si l’analyse des IDN (Internationalized Domain Name) est appliquée à un nom de domaine. la valeur par défaut est None.</span><span class="sxs-lookup"><span data-stu-id="3e71f-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e71f-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3e71f-115">Child Elements</span></span>  
 <span data-ttu-id="3e71f-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="3e71f-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e71f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3e71f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3e71f-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="3e71f-118">**Element**</span></span>|<span data-ttu-id="3e71f-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="3e71f-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3e71f-120">URI</span><span class="sxs-lookup"><span data-stu-id="3e71f-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="3e71f-121">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="3e71f-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e71f-122">Notes</span><span class="sxs-lookup"><span data-stu-id="3e71f-122">Remarks</span></span>  
 <span data-ttu-id="3e71f-123">La classe <xref:System.Uri> existante a été étendue dans .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="3e71f-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="3e71f-124">3,0 SP1 et 2,0 SP1 avec prise en charge des IRI (International Resource Identifiers) et des noms de domaine internationaux (IDN).</span><span class="sxs-lookup"><span data-stu-id="3e71f-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="3e71f-125">Les utilisateurs actuels ne voient aucune modification du comportement .NET Framework 2,0, sauf s’ils activent spécifiquement la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="3e71f-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="3e71f-126">Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e71f-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="3e71f-127">Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises:</span><span class="sxs-lookup"><span data-stu-id="3e71f-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="3e71f-128">Ajoutez la ligne suivante au fichier machine. config dans le répertoire .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="3e71f-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="3e71f-129">Spécifiez si vous souhaitez appliquer l’analyse des IDN (Internationalized Domain Name) au nom de domaine et si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="3e71f-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="3e71f-130">Cela est spécifié dans le fichier machine.config ou app.config.</span><span class="sxs-lookup"><span data-stu-id="3e71f-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="3e71f-131">Il existe trois valeurs possibles pour l’IDN selon les serveurs DNS utilisés:</span><span class="sxs-lookup"><span data-stu-id="3e71f-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
- <span data-ttu-id="3e71f-132">IDN activé = tous</span><span class="sxs-lookup"><span data-stu-id="3e71f-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="3e71f-133">Cette valeur convertit tous les noms de domaine Unicode en leurs équivalents Punycode (noms IDN).</span><span class="sxs-lookup"><span data-stu-id="3e71f-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
- <span data-ttu-id="3e71f-134">IDN activé = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="3e71f-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="3e71f-135">Cette valeur convertit tous les noms de domaine Unicode qui ne se trouvent pas sur l’intranet local pour utiliser les équivalents Punycode (noms IDN).</span><span class="sxs-lookup"><span data-stu-id="3e71f-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="3e71f-136">Dans ce cas, pour gérer les noms internationaux sur l’intranet local, les serveurs DNS utilisés pour l’intranet doivent prendre en charge la résolution de noms Unicode.</span><span class="sxs-lookup"><span data-stu-id="3e71f-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
- <span data-ttu-id="3e71f-137">IDN activé = aucun</span><span class="sxs-lookup"><span data-stu-id="3e71f-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="3e71f-138">Cette valeur ne convertit pas les noms de domaine Unicode pour utiliser Punycode.</span><span class="sxs-lookup"><span data-stu-id="3e71f-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="3e71f-139">Il s’agit de la valeur par défaut qui est cohérente avec le comportement .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="3e71f-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="3e71f-140">L’activation des IDN entraîne la conversion de toutes les étiquettes Unicode d’un nom de domaine en leurs équivalents Punycode.</span><span class="sxs-lookup"><span data-stu-id="3e71f-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="3e71f-141">Les noms Punycode contiennent uniquement des caractères ASCII et commencent toujours par le préfixe xn--.</span><span class="sxs-lookup"><span data-stu-id="3e71f-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="3e71f-142">Cela permet de garantir la prise en charge des serveurs DNS existants sur Internet, la plupart d’entre eux prenant uniquement en charge les caractères ASCII (consultez la norme RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="3e71f-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="3e71f-143">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3e71f-143">Configuration Files</span></span>  
 <span data-ttu-id="3e71f-144">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="3e71f-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e71f-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="3e71f-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3e71f-146">Description</span><span class="sxs-lookup"><span data-stu-id="3e71f-146">Description</span></span>  
 <span data-ttu-id="3e71f-147">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse des IRI et les noms IDN.</span><span class="sxs-lookup"><span data-stu-id="3e71f-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3e71f-148">Code</span><span class="sxs-lookup"><span data-stu-id="3e71f-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e71f-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e71f-149">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="3e71f-150">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3e71f-150">Network Settings Schema</span></span>](index.md)
