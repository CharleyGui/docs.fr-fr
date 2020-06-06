---
title: <idn>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698170"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="a60c7-102">\<idn>, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="a60c7-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="a60c7-103">Spécifie si l’analyse des IDN (Internationalized Domain Name) est appliquée à un nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="a60c7-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a><span data-ttu-id="a60c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a60c7-104">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a60c7-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a60c7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a60c7-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a60c7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a60c7-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a60c7-107">Attributes</span></span>  

|<span data-ttu-id="a60c7-108">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="a60c7-108">**Element**</span></span>|<span data-ttu-id="a60c7-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="a60c7-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="a60c7-110">Spécifie si l’analyse des IDN (Internationalized Domain Name) est appliquée à un nom de domaine. la valeur par défaut est None.</span><span class="sxs-lookup"><span data-stu-id="a60c7-110">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="a60c7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a60c7-111">Child elements</span></span>

<span data-ttu-id="a60c7-112">Aucune</span><span class="sxs-lookup"><span data-stu-id="a60c7-112">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="a60c7-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a60c7-113">Parent elements</span></span>

|<span data-ttu-id="a60c7-114">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="a60c7-114">**Element**</span></span>|<span data-ttu-id="a60c7-115">**Description**</span><span class="sxs-lookup"><span data-stu-id="a60c7-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a60c7-116">uri</span><span class="sxs-lookup"><span data-stu-id="a60c7-116">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="a60c7-117">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="a60c7-117">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="a60c7-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="a60c7-118">Remarks</span></span>

<span data-ttu-id="a60c7-119">La <xref:System.Uri> classe existante a été étendue dans .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="a60c7-119">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="a60c7-120">3,0 SP1 et 2,0 SP1 avec prise en charge des IRI (International Resource Identifiers) et des noms de domaine internationaux (IDN).</span><span class="sxs-lookup"><span data-stu-id="a60c7-120">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="a60c7-121">Les utilisateurs actuels ne voient aucune modification du comportement .NET Framework 2,0, sauf s’ils activent spécifiquement la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="a60c7-121">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="a60c7-122">Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a60c7-122">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="a60c7-123">Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="a60c7-123">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="a60c7-124">Ajoutez la ligne suivante au fichier machine. config dans le répertoire .NET Framework 2,0 :</span><span class="sxs-lookup"><span data-stu-id="a60c7-124">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="a60c7-125">Spécifiez si vous souhaitez appliquer l’analyse des IDN (Internationalized Domain Name) au nom de domaine et si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="a60c7-125">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="a60c7-126">Cela est spécifié dans le fichier machine.config ou app.config.</span><span class="sxs-lookup"><span data-stu-id="a60c7-126">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="a60c7-127">Il existe trois valeurs possibles pour l’IDN selon les serveurs DNS utilisés :</span><span class="sxs-lookup"><span data-stu-id="a60c7-127">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="a60c7-128">IDN activé = tous</span><span class="sxs-lookup"><span data-stu-id="a60c7-128">idn enabled = All</span></span>  

     <span data-ttu-id="a60c7-129">Cette valeur convertit tous les noms de domaine Unicode en leurs équivalents Punycode (noms IDN).</span><span class="sxs-lookup"><span data-stu-id="a60c7-129">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="a60c7-130">IDN activé = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="a60c7-130">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="a60c7-131">Cette valeur convertit tous les noms de domaine Unicode qui ne se trouvent pas sur l’intranet local pour utiliser les équivalents Punycode (noms IDN).</span><span class="sxs-lookup"><span data-stu-id="a60c7-131">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="a60c7-132">Dans ce cas, pour gérer les noms internationaux sur l’intranet local, les serveurs DNS utilisés pour l’intranet doivent prendre en charge la résolution de noms Unicode.</span><span class="sxs-lookup"><span data-stu-id="a60c7-132">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="a60c7-133">IDN activé = aucun</span><span class="sxs-lookup"><span data-stu-id="a60c7-133">idn enabled = None</span></span>

     <span data-ttu-id="a60c7-134">Cette valeur ne convertit aucun nom de domaine Unicode pour utiliser Punycode.</span><span class="sxs-lookup"><span data-stu-id="a60c7-134">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="a60c7-135">Il s'agit de la valeur par défaut cohérente avec le comportement du .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="a60c7-135">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="a60c7-136">L’activation des IDN entraîne la conversion de toutes les étiquettes Unicode d’un nom de domaine en leurs équivalents Punycode.</span><span class="sxs-lookup"><span data-stu-id="a60c7-136">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="a60c7-137">Les noms Punycode contiennent uniquement des caractères ASCII et commencent toujours par le préfixe xn--.</span><span class="sxs-lookup"><span data-stu-id="a60c7-137">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="a60c7-138">Cela permet de garantir la prise en charge des serveurs DNS existants sur Internet, la plupart d’entre eux prenant uniquement en charge les caractères ASCII (consultez la norme RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="a60c7-138">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="a60c7-139">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a60c7-139">Configuration files</span></span>

<span data-ttu-id="a60c7-140">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a60c7-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="a60c7-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="a60c7-141">Example</span></span>

<span data-ttu-id="a60c7-142">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse des IRI et les noms IDN :</span><span class="sxs-lookup"><span data-stu-id="a60c7-142">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a60c7-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a60c7-143">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="a60c7-144">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a60c7-144">Network Settings Schema</span></span>](index.md)
