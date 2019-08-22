---
title: <add>, élément de schemeSettings (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 027c7aaffea7950739f532309255d77afa031ada
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659551"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="225b4-102">\<Ajouter > élément pour schemeSettings (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="225b4-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="225b4-103">Ajoute un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="225b4-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="225b4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="225b4-104">\<configuration></span></span>  
<span data-ttu-id="225b4-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="225b4-105">\<uri></span></span>  
<span data-ttu-id="225b4-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="225b4-106">\<schemeSettings></span></span>  
<span data-ttu-id="225b4-107">\<add></span><span class="sxs-lookup"><span data-stu-id="225b4-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="225b4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="225b4-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="225b4-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="225b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="225b4-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="225b4-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="225b4-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="225b4-111">Attributes</span></span>  
  
|<span data-ttu-id="225b4-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="225b4-112">Attribute</span></span>|<span data-ttu-id="225b4-113">Description</span><span class="sxs-lookup"><span data-stu-id="225b4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="225b4-114">name</span><span class="sxs-lookup"><span data-stu-id="225b4-114">name</span></span>|<span data-ttu-id="225b4-115">Nom du schéma auquel ce paramètre s’applique.</span><span class="sxs-lookup"><span data-stu-id="225b4-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="225b4-116">Les seules valeurs prises en charge sont Name = "http" et Name = "https".</span><span class="sxs-lookup"><span data-stu-id="225b4-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="225b4-117">{Nom de l’attribut} Attribut</span><span class="sxs-lookup"><span data-stu-id="225b4-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="225b4-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="225b4-118">Value</span></span>|<span data-ttu-id="225b4-119">Description</span><span class="sxs-lookup"><span data-stu-id="225b4-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="225b4-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="225b4-120">genericUriParserOptions</span></span>|<span data-ttu-id="225b4-121">Options de l’analyseur pour ce schéma.</span><span class="sxs-lookup"><span data-stu-id="225b4-121">The parser options for this scheme.</span></span> <span data-ttu-id="225b4-122">La seule valeur prise en charge est genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="225b4-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="225b4-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="225b4-123">Child Elements</span></span>  
 <span data-ttu-id="225b4-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="225b4-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="225b4-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="225b4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="225b4-126">Élément</span><span class="sxs-lookup"><span data-stu-id="225b4-126">Element</span></span>|<span data-ttu-id="225b4-127">Description</span><span class="sxs-lookup"><span data-stu-id="225b4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="225b4-128">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="225b4-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="225b4-129">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="225b4-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="225b4-130">Notes</span><span class="sxs-lookup"><span data-stu-id="225b4-130">Remarks</span></span>  
 <span data-ttu-id="225b4-131">Par défaut, la <xref:System.Uri?displayProperty=nameWithType> classe annule l’échappement des délimiteurs de chemin d’accès encodés en pourcentage avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="225b4-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="225b4-132">Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes:</span><span class="sxs-lookup"><span data-stu-id="225b4-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="225b4-133">Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur:</span><span class="sxs-lookup"><span data-stu-id="225b4-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="225b4-134">Pour cette raison, <xref:System.Uri?displayProperty=nameWithType> la classe First annule les délimiteurs de chemin d’accès, puis applique la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="225b4-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="225b4-135">Le résultat de la transmission de l’URL malveillante ci-dessus au <xref:System.Uri?displayProperty=nameWithType> constructeur de classe génère l’URI suivant:</span><span class="sxs-lookup"><span data-stu-id="225b4-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="225b4-136">Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="225b4-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="225b4-137">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="225b4-137">Configuration Files</span></span>  
 <span data-ttu-id="225b4-138">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="225b4-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="225b4-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="225b4-139">Example</span></span>  
 <span data-ttu-id="225b4-140">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge la non-échappement des délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="225b4-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="225b4-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="225b4-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="225b4-142">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="225b4-142">Network Settings Schema</span></span>](index.md)
