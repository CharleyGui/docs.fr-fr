---
title: <idn>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698170"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="561ee-102">\<idn >, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="561ee-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="561ee-103">Spécifie si l’analyse des IDN (Internationalized Domain Name) est appliquée à un nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="561ee-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[<span data-ttu-id="561ee-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="561ee-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="561ee-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="561ee-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="561ee-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<idn >**</span><span class="sxs-lookup"><span data-stu-id="561ee-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="561ee-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="561ee-107">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="561ee-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="561ee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="561ee-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="561ee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="561ee-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="561ee-110">Attributes</span></span>  

|<span data-ttu-id="561ee-111">**Élément**</span><span class="sxs-lookup"><span data-stu-id="561ee-111">**Element**</span></span>|<span data-ttu-id="561ee-112">**Description**</span><span class="sxs-lookup"><span data-stu-id="561ee-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="561ee-113">Spécifie si l’analyse des IDN (Internationalized Domain Name) est appliquée à un nom de domaine. la valeur par défaut est None.</span><span class="sxs-lookup"><span data-stu-id="561ee-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="561ee-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="561ee-114">Child elements</span></span>

<span data-ttu-id="561ee-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="561ee-115">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="561ee-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="561ee-116">Parent elements</span></span>

|<span data-ttu-id="561ee-117">**Élément**</span><span class="sxs-lookup"><span data-stu-id="561ee-117">**Element**</span></span>|<span data-ttu-id="561ee-118">**Description**</span><span class="sxs-lookup"><span data-stu-id="561ee-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="561ee-119">URI</span><span class="sxs-lookup"><span data-stu-id="561ee-119">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="561ee-120">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="561ee-120">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="561ee-121">Notes</span><span class="sxs-lookup"><span data-stu-id="561ee-121">Remarks</span></span>

<span data-ttu-id="561ee-122">La classe <xref:System.Uri> existante a été étendue dans .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="561ee-122">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="561ee-123">3,0 SP1 et 2,0 SP1 avec prise en charge des IRI (International Resource Identifiers) et des noms de domaine internationaux (IDN).</span><span class="sxs-lookup"><span data-stu-id="561ee-123">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="561ee-124">Les utilisateurs actuels ne voient aucune modification du comportement .NET Framework 2,0, sauf s’ils activent spécifiquement la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="561ee-124">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="561ee-125">Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="561ee-125">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="561ee-126">Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="561ee-126">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="561ee-127">Ajoutez la ligne suivante au fichier machine. config dans le répertoire .NET Framework 2,0 :</span><span class="sxs-lookup"><span data-stu-id="561ee-127">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="561ee-128">Spécifiez si vous souhaitez appliquer l’analyse des IDN (Internationalized Domain Name) au nom de domaine et si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="561ee-128">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="561ee-129">Cela est spécifié dans le fichier machine.config ou app.config.</span><span class="sxs-lookup"><span data-stu-id="561ee-129">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="561ee-130">Il existe trois valeurs possibles pour l’IDN selon les serveurs DNS utilisés :</span><span class="sxs-lookup"><span data-stu-id="561ee-130">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="561ee-131">IDN activé = tous</span><span class="sxs-lookup"><span data-stu-id="561ee-131">idn enabled = All</span></span>  

     <span data-ttu-id="561ee-132">Cette valeur convertit tous les noms de domaine Unicode en leurs équivalents Punycode (noms IDN).</span><span class="sxs-lookup"><span data-stu-id="561ee-132">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="561ee-133">IDN activé = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="561ee-133">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="561ee-134">Cette valeur convertit tous les noms de domaine Unicode qui ne se trouvent pas sur l’intranet local pour utiliser les équivalents Punycode (noms IDN).</span><span class="sxs-lookup"><span data-stu-id="561ee-134">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="561ee-135">Dans ce cas, pour gérer les noms internationaux sur l’intranet local, les serveurs DNS utilisés pour l’intranet doivent prendre en charge la résolution de noms Unicode.</span><span class="sxs-lookup"><span data-stu-id="561ee-135">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="561ee-136">IDN activé = aucun</span><span class="sxs-lookup"><span data-stu-id="561ee-136">idn enabled = None</span></span>

     <span data-ttu-id="561ee-137">Cette valeur ne convertit pas les noms de domaine Unicode pour utiliser Punycode.</span><span class="sxs-lookup"><span data-stu-id="561ee-137">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="561ee-138">Il s’agit de la valeur par défaut qui est cohérente avec le comportement .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="561ee-138">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="561ee-139">L’activation des IDN entraîne la conversion de toutes les étiquettes Unicode d’un nom de domaine en leurs équivalents Punycode.</span><span class="sxs-lookup"><span data-stu-id="561ee-139">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="561ee-140">Les noms Punycode contiennent uniquement des caractères ASCII et commencent toujours par le préfixe xn--.</span><span class="sxs-lookup"><span data-stu-id="561ee-140">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="561ee-141">Cela permet de garantir la prise en charge des serveurs DNS existants sur Internet, la plupart d’entre eux prenant uniquement en charge les caractères ASCII (consultez la norme RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="561ee-141">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="561ee-142">Les fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="561ee-142">Configuration files</span></span>

<span data-ttu-id="561ee-143">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="561ee-143">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="561ee-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="561ee-144">Example</span></span>

<span data-ttu-id="561ee-145">L’exemple suivant illustre une configuration utilisée par la classe <xref:System.Uri> pour prendre en charge l’analyse des IRI et les noms IDN :</span><span class="sxs-lookup"><span data-stu-id="561ee-145">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="561ee-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="561ee-146">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="561ee-147">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="561ee-147">Network Settings Schema</span></span>](index.md)
