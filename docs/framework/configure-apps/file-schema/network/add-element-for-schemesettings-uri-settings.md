---
title: <add>, élément de schemeSettings (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: efd52557ea8b617a39e685ff8ad69bab01322a7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699595"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="f9ae1-102">Élément @no__t 0add > pour schemeSettings (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="f9ae1-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="f9ae1-103">Ajoute un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-103">Adds a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="f9ae1-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="f9ae1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f9ae1-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f9ae1-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="f9ae1-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f9ae1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="f9ae1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="f9ae1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ae1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9ae1-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9ae1-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f9ae1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f9ae1-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9ae1-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f9ae1-111">Attributes</span></span>  
  
|<span data-ttu-id="f9ae1-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9ae1-112">Attribute</span></span>|<span data-ttu-id="f9ae1-113">Description</span><span class="sxs-lookup"><span data-stu-id="f9ae1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9ae1-114">name</span><span class="sxs-lookup"><span data-stu-id="f9ae1-114">name</span></span>|<span data-ttu-id="f9ae1-115">Nom du schéma auquel ce paramètre s’applique.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="f9ae1-116">Les seules valeurs prises en charge sont Name = "http" et Name = "https".</span><span class="sxs-lookup"><span data-stu-id="f9ae1-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="f9ae1-117">{Nom de l’attribut} Attribut</span><span class="sxs-lookup"><span data-stu-id="f9ae1-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="f9ae1-118">Value</span><span class="sxs-lookup"><span data-stu-id="f9ae1-118">Value</span></span>|<span data-ttu-id="f9ae1-119">Description</span><span class="sxs-lookup"><span data-stu-id="f9ae1-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f9ae1-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="f9ae1-120">genericUriParserOptions</span></span>|<span data-ttu-id="f9ae1-121">Options de l’analyseur pour ce schéma.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-121">The parser options for this scheme.</span></span> <span data-ttu-id="f9ae1-122">La seule valeur prise en charge est genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="f9ae1-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9ae1-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f9ae1-123">Child Elements</span></span>  
 <span data-ttu-id="f9ae1-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9ae1-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f9ae1-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f9ae1-126">Élément</span><span class="sxs-lookup"><span data-stu-id="f9ae1-126">Element</span></span>|<span data-ttu-id="f9ae1-127">Description</span><span class="sxs-lookup"><span data-stu-id="f9ae1-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9ae1-128">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="f9ae1-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="f9ae1-129">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9ae1-130">Notes</span><span class="sxs-lookup"><span data-stu-id="f9ae1-130">Remarks</span></span>  
 <span data-ttu-id="f9ae1-131">Par défaut, la classe <xref:System.Uri?displayProperty=nameWithType> annule l’échappement des délimiteurs de chemin d’accès encodés en pourcentage avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="f9ae1-132">Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f9ae1-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f9ae1-133">Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur :</span><span class="sxs-lookup"><span data-stu-id="f9ae1-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="f9ae1-134">C’est la raison pour laquelle la classe <xref:System.Uri?displayProperty=nameWithType> n’ignore pas les délimiteurs de chemin d’accès, puis applique la compression de chemin.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="f9ae1-135">Le résultat de la transmission de l’URL malveillante ci-dessus au constructeur de classe <xref:System.Uri?displayProperty=nameWithType> génère l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="f9ae1-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f9ae1-136">Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f9ae1-137">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="f9ae1-137">Configuration Files</span></span>  
 <span data-ttu-id="f9ae1-138">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f9ae1-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9ae1-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9ae1-139">Example</span></span>  
 <span data-ttu-id="f9ae1-140">L’exemple suivant illustre une configuration utilisée par la classe <xref:System.Uri> pour ne pas prendre en charge l’échappement des délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="f9ae1-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9ae1-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9ae1-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="f9ae1-142">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="f9ae1-142">Network Settings Schema</span></span>](index.md)
