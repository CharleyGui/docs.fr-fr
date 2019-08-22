---
title: <clear>, élément de schemeSettings (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 51c669aff767948523172aa075677ad3fb6478a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664179"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="64144-102">\<Clear >, élément de schemeSettings (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="64144-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="64144-103">Efface tous les paramètres de schéma existants.</span><span class="sxs-lookup"><span data-stu-id="64144-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="64144-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="64144-104">\<configuration></span></span>  
<span data-ttu-id="64144-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="64144-105">\<uri></span></span>  
<span data-ttu-id="64144-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="64144-106">\<schemeSettings></span></span>  
<span data-ttu-id="64144-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="64144-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64144-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64144-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64144-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="64144-109">Attributes and Elements</span></span>  
 <span data-ttu-id="64144-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="64144-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64144-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="64144-111">Attributes</span></span>  
 <span data-ttu-id="64144-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="64144-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64144-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="64144-113">Child Elements</span></span>  
 <span data-ttu-id="64144-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="64144-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64144-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="64144-115">Parent Elements</span></span>  
  
|<span data-ttu-id="64144-116">Élément</span><span class="sxs-lookup"><span data-stu-id="64144-116">Element</span></span>|<span data-ttu-id="64144-117">Description</span><span class="sxs-lookup"><span data-stu-id="64144-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64144-118">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="64144-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="64144-119">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="64144-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64144-120">Notes</span><span class="sxs-lookup"><span data-stu-id="64144-120">Remarks</span></span>  
 <span data-ttu-id="64144-121">Par défaut, la <xref:System.Uri?displayProperty=nameWithType> classe annule l’échappement des délimiteurs de chemin d’accès encodés en pourcentage avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="64144-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="64144-122">Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes:</span><span class="sxs-lookup"><span data-stu-id="64144-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="64144-123">Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur:</span><span class="sxs-lookup"><span data-stu-id="64144-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="64144-124">Pour cette raison, <xref:System.Uri?displayProperty=nameWithType> la classe First annule les délimiteurs de chemin d’accès, puis applique la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="64144-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="64144-125">Le résultat de la transmission de l’URL malveillante ci-dessus au <xref:System.Uri?displayProperty=nameWithType> constructeur de classe génère l’URI suivant:</span><span class="sxs-lookup"><span data-stu-id="64144-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="64144-126">Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="64144-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="64144-127">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="64144-127">Configuration Files</span></span>  
 <span data-ttu-id="64144-128">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="64144-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64144-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="64144-129">Example</span></span>  
 <span data-ttu-id="64144-130">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe qui efface tous les paramètres de schéma, puis ajoute la prise en charge pour ne pas échapper les délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="64144-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64144-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64144-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="64144-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="64144-132">Network Settings Schema</span></span>](index.md)
