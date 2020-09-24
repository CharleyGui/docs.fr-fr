---
title: <add>, élément de schemeSettings (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 55fcba41d4dabf8937ebaa11235e9309bcb57952
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149459"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="b6a91-102">\<add>, élément de schemeSettings (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="b6a91-102">\<add> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="b6a91-103">Ajoute un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="b6a91-103">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="b6a91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6a91-104">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6a91-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b6a91-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b6a91-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b6a91-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6a91-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6a91-107">Attributes</span></span>  
  
|<span data-ttu-id="b6a91-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b6a91-108">Attribute</span></span>|<span data-ttu-id="b6a91-109">Description</span><span class="sxs-lookup"><span data-stu-id="b6a91-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6a91-110">name</span><span class="sxs-lookup"><span data-stu-id="b6a91-110">name</span></span>|<span data-ttu-id="b6a91-111">Nom du schéma auquel ce paramètre s’applique.</span><span class="sxs-lookup"><span data-stu-id="b6a91-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="b6a91-112">Les seules valeurs prises en charge sont Name = "http" et Name = "https".</span><span class="sxs-lookup"><span data-stu-id="b6a91-112">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="b6a91-113">{Nom de l’attribut} Attribut</span><span class="sxs-lookup"><span data-stu-id="b6a91-113">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="b6a91-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="b6a91-114">Value</span></span>|<span data-ttu-id="b6a91-115">Description</span><span class="sxs-lookup"><span data-stu-id="b6a91-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b6a91-116">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="b6a91-116">genericUriParserOptions</span></span>|<span data-ttu-id="b6a91-117">Options de l’analyseur pour ce schéma.</span><span class="sxs-lookup"><span data-stu-id="b6a91-117">The parser options for this scheme.</span></span> <span data-ttu-id="b6a91-118">La seule valeur prise en charge est genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="b6a91-118">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6a91-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b6a91-119">Child Elements</span></span>  

 <span data-ttu-id="b6a91-120">None</span><span class="sxs-lookup"><span data-stu-id="b6a91-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6a91-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b6a91-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b6a91-122">Élément</span><span class="sxs-lookup"><span data-stu-id="b6a91-122">Element</span></span>|<span data-ttu-id="b6a91-123">Description</span><span class="sxs-lookup"><span data-stu-id="b6a91-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6a91-124">\<schemeSettings> , Élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="b6a91-124">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="b6a91-125">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b6a91-125">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6a91-126">Notes</span><span class="sxs-lookup"><span data-stu-id="b6a91-126">Remarks</span></span>  

 <span data-ttu-id="b6a91-127">Par défaut, la <xref:System.Uri?displayProperty=nameWithType> classe annule l’échappement des délimiteurs de chemin d’accès encodés en pourcentage avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="b6a91-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="b6a91-128">Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6a91-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="b6a91-129">Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur :</span><span class="sxs-lookup"><span data-stu-id="b6a91-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="b6a91-130">Pour cette raison, la <xref:System.Uri?displayProperty=nameWithType> classe First annule les délimiteurs de chemin d’accès, puis applique la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="b6a91-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="b6a91-131">Le résultat de la transmission de l’URL malveillante ci-dessus au <xref:System.Uri?displayProperty=nameWithType> constructeur de classe génère l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="b6a91-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="b6a91-132">Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="b6a91-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b6a91-133">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b6a91-133">Configuration Files</span></span>  

 <span data-ttu-id="b6a91-134">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b6a91-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6a91-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6a91-135">Example</span></span>  

 <span data-ttu-id="b6a91-136">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge la non-échappement des délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="b6a91-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6a91-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6a91-137">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="b6a91-138">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="b6a91-138">Network Settings Schema</span></span>](index.md)
