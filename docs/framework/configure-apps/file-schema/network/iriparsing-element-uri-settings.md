---
title: <iriParsing>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698090"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="3745a-102">\<iriParsing>, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="3745a-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="3745a-103">Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.</span><span class="sxs-lookup"><span data-stu-id="3745a-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a><span data-ttu-id="3745a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3745a-104">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3745a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3745a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3745a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3745a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3745a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="3745a-107">Attributes</span></span>  
  
|<span data-ttu-id="3745a-108">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="3745a-108">**Element**</span></span>|<span data-ttu-id="3745a-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="3745a-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="3745a-110">Spécifie si l’analyse IRI est activée.</span><span class="sxs-lookup"><span data-stu-id="3745a-110">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="3745a-111">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="3745a-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3745a-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3745a-112">Child Elements</span></span>  
 <span data-ttu-id="3745a-113">Aucune</span><span class="sxs-lookup"><span data-stu-id="3745a-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3745a-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3745a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="3745a-115">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="3745a-115">**Element**</span></span>|<span data-ttu-id="3745a-116">**Description**</span><span class="sxs-lookup"><span data-stu-id="3745a-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3745a-117">uri</span><span class="sxs-lookup"><span data-stu-id="3745a-117">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="3745a-118">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="3745a-118">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3745a-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="3745a-119">Remarks</span></span>  
 <span data-ttu-id="3745a-120">La <xref:System.Uri> classe existante a été étendue dans .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="3745a-120">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="3745a-121">3,0 SP1 et 2,0 SP1 pour assurer la prise en charge des IRI (International Resource Identifier) et des noms de domaine internationaux (IDN).</span><span class="sxs-lookup"><span data-stu-id="3745a-121">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="3745a-122">Les utilisateurs actuels ne voient aucune modification du comportement .NET Framework 2,0, sauf s’ils activent spécifiquement la prise en charge des IRI et des IDN.</span><span class="sxs-lookup"><span data-stu-id="3745a-122">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="3745a-123">Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3745a-123">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="3745a-124">Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="3745a-124">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="3745a-125">Ajoutez la ligne suivante au fichier machine. config dans le répertoire .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="3745a-125">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="3745a-126">Spécifie si les règles d’analyse IRI doivent être appliquées.</span><span class="sxs-lookup"><span data-stu-id="3745a-126">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="3745a-127">Cela est spécifié dans le fichier machine.config ou app.config.</span><span class="sxs-lookup"><span data-stu-id="3745a-127">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="3745a-128">L’activation de l’analyse IRI (iriParsing enabled = `true` ) effectue la normalisation et la vérification des caractères selon les dernières règles IRI de la norme RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="3745a-128">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="3745a-129">La valeur par défaut est et effectue la `false` normalisation et la vérification des caractères selon les spécifications rfc 2396 et rfc 3986 (pour les littéraux IPv6).</span><span class="sxs-lookup"><span data-stu-id="3745a-129">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="3745a-130">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3745a-130">Configuration Files</span></span>  
 <span data-ttu-id="3745a-131">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="3745a-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3745a-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="3745a-132">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3745a-133">Description</span><span class="sxs-lookup"><span data-stu-id="3745a-133">Description</span></span>  
 <span data-ttu-id="3745a-134">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse des IRI et les noms IDN.</span><span class="sxs-lookup"><span data-stu-id="3745a-134">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3745a-135">Code</span><span class="sxs-lookup"><span data-stu-id="3745a-135">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3745a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3745a-136">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="3745a-137">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3745a-137">Network Settings Schema</span></span>](index.md)
