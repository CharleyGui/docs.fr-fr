---
title: <schemeSettings>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 498aef77a1dfd8cffcac73b704b8d1bb6df5d165
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697767"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="0bb79-102">\<élément schemeSettings > (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="0bb79-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="0bb79-103">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0bb79-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[<span data-ttu-id="0bb79-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="0bb79-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0bb79-105">&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0bb79-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="0bb79-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<schemeSettings** ></span><span class="sxs-lookup"><span data-stu-id="0bb79-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb79-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bb79-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bb79-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0bb79-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0bb79-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0bb79-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bb79-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="0bb79-110">Attributes</span></span>  
 <span data-ttu-id="0bb79-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="0bb79-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0bb79-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0bb79-112">Child Elements</span></span>  
  
|<span data-ttu-id="0bb79-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="0bb79-113">**Element**</span></span>|<span data-ttu-id="0bb79-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="0bb79-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0bb79-115">add</span><span class="sxs-lookup"><span data-stu-id="0bb79-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="0bb79-116">Ajoute un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="0bb79-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="0bb79-117">clear</span><span class="sxs-lookup"><span data-stu-id="0bb79-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="0bb79-118">Efface tous les paramètres de schéma existants.</span><span class="sxs-lookup"><span data-stu-id="0bb79-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="0bb79-119">remove</span><span class="sxs-lookup"><span data-stu-id="0bb79-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="0bb79-120">Supprime un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="0bb79-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0bb79-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0bb79-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0bb79-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="0bb79-122">**Element**</span></span>|<span data-ttu-id="0bb79-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="0bb79-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0bb79-124">URI</span><span class="sxs-lookup"><span data-stu-id="0bb79-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="0bb79-125">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="0bb79-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bb79-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="0bb79-126">Remarks</span></span>  
 <span data-ttu-id="0bb79-127">Par défaut, la classe <xref:System.Uri?displayProperty=nameWithType> annule les délimiteurs de chemin d’accès encodés de pourcentage avant l’exécution de la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0bb79-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="0bb79-128">Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bb79-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0bb79-129">Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur :</span><span class="sxs-lookup"><span data-stu-id="0bb79-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="0bb79-130">C’est pourquoi <xref:System.Uri?displayProperty=nameWithType> classe First annule les délimiteurs de chemin d’accès, puis applique la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0bb79-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="0bb79-131">Le résultat de la transmission de l’URL malveillante ci-dessus à <xref:System.Uri?displayProperty=nameWithType> constructeur de classe génère l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="0bb79-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0bb79-132">Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="0bb79-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0bb79-133">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0bb79-133">Configuration Files</span></span>  
 <span data-ttu-id="0bb79-134">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0bb79-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bb79-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="0bb79-135">Example</span></span>  
 <span data-ttu-id="0bb79-136">L’exemple suivant illustre une configuration utilisée par la classe <xref:System.Uri> pour prendre en charge l’échappement des délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="0bb79-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="0bb79-137">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="0bb79-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="0bb79-138">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="0bb79-138">Namespace</span></span>|<span data-ttu-id="0bb79-139">System</span><span class="sxs-lookup"><span data-stu-id="0bb79-139">System</span></span>|  
|<span data-ttu-id="0bb79-140">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="0bb79-140">Schema Name</span></span>||  
|<span data-ttu-id="0bb79-141">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="0bb79-141">Validation File</span></span>||  
|<span data-ttu-id="0bb79-142">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="0bb79-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="0bb79-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bb79-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="0bb79-144">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="0bb79-144">Network Settings Schema</span></span>](index.md)
